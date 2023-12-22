---
Network: TCP
(OS) Operating Systems: Linux
---
#CS #hard_interrupts #soft_interrupts 
For any details refer [[Linux and Windows Kernel Comparison]].
[Youtube Link](https://www.youtube.com/watch?v=ck4WvYM9V4c)

Tools: NCAT, LTTng, Trace Compass, Wireshark
## Experiment: 
Client and Server side NCAT, connected over TCP. Trace server side application when there is a TCP SYN request and look at how kernel handles that. Then send data to client.
**NCAT**: Networking utility that can send data back and forth between client and server over TCP and UDP.

**LTTng**: Tracer to trace kernel.

**Trace Compass**: Eclipse open source tool, to provide insights in traces collected.


## Running the Experiment

```Server
ncat --listen 192.168.1.105 5000
```

```Client
ncat 192.168.1.105 5000
```
192.168.1.105: address I want to bind to. local address.
5000: local port
This created the connection. And then I can simply type in to the terminal and can test.

## Packet Trace (*Wireshark*)

1. TCP [SYN, Len:0]: recvd from the remote side that will signal server, that "hey, I want to connect with you".
2. TCP [SYN, ACK:1,Len:0]: Acknowledged from server to client.
3. TCP [ACK:1,Len:0]: Acknowledged from client to server.
*At this point the TCP is established. This is so called TCP Handshake.*
*Now for eg. I typed **Hello** on sever side and press enter*
4. TCP [PSH, ACK:1,Len:6]: Len 6 byte packet from server to client. Generally, TCP waits for more packets but NCAT pushed everything to communication channel on enter so, as soon as we press enter the data got sent to the client.
5. TCP [ACK:7,Len:0]: Client say, I have recvd everything before 7th byte and waiting for that.
*I now disconnect from client side*
6. TCP [RST,ACK,ACK:7,Len:0]: Disconnect from the client to server.


## Kernel Trace (*Trace Compass*)

1. **exec** system call by bash to load up nat binaries and start it...linux process creation
2. **socket** system call: system call made by ncat process
	1. event type = syscall_entry_socket
	2. family : 2 = IPv4 family
	3. event type = syscall_exit_socket, with return file descriptor.
3. **setsocketopt** system call: it has multiple events too.
4. **bind** system call: binds that socket to the IP and Port
5. **listen** system call: listens for any TCP request.
6. **fcntl** system calls: for setting some flags.
7. **select** system call: it waits for a number of file descriptor for read or write events. It wants to wait of assigned descriptor in step2 for read ready. This is where we go in action where ncat is listening to any request made to the server
   *Post this ncat will be taken from run queue of CPU as it will be blocked.*
8. **wake** event when a SYN request comes up, so the kernel will run this to give me the CPU. Some more events take place. This is just after the SYN request came.
	* hardware interrupt, that starts everything. Withing microseconds.
	* network receive interrupt
9. **select** system call: return the number of file descriptor among the watched have something interesting.
10. **accept** system call: to accept the SYN request. For any new connection request to the listening socket the new data socket gets created for that request attached to that existing socket. So accept will return the file descriptor for that data socket.
11. **close**  system call: specific to ncat, it closes the listen socket. NCAT only has 1 connection at one time so it happens, in general it will not happen.
12. **select** system call: It will wait for something to happen on the connection. But this time we will not wait for something to happen on the file descriptor in step2 as that is closed due to ncat limitations. We will listen for the file descriptor we got int step10 and file descriptor 0 which is STDIN. So, because ncat says I am waiting for something to come from the client side or the server side to client.
    *I typed something after this from the server side*
13. **read** system call: reads from the file with given descriptor which is 0 for STDIN in our case. Returns the number of bytes read.
14. **fcntl** system call: for setting some flags.
15. **sendto** system call: sends something over the network. executed on the data socket file descriptor that is the one we got in step10. Returns the number of bytes send.
16. **select** system call: on the data socket and STDIN. waiting for something to happen. After this it goes in blocking.
17. **wake**: somewhere just after the reset packet from the client to the server.
18. **select** system call: something came from the other side over the data socket. 
19. **recvfrom** system call:
20. **close** system call:
21. **exit_group** system call: but this is how ncat behaves when clients hangs up, normal server generally wont do this.

## Deeper Dive
![[Pasted image 20231120171349.png]]
We can go from a file descriptor to what is actually is using lttng_statedump events. One dump per process.
File descriptors are **processed scoped**, so, two different processes can have same descriptors but assigned to different files. But if we have different threads then those are under process scope so, descriptors will be same for threads of a process.
```pid
pidof ncat
```
say you get 33706
```List fd
ls -l /proc/33706/fd
```
It will list all the file descriptors associated with this.
You will see **inode number** for the socket there.

### What happens on the arrival of the first *SYN*?
So, a separate CPU thread gets an interrupt, and I enter in hardware interrupt service routine. It then raises a software interrupt for the Network Recv.
In software interrupt, I enter and exit from the network recv, then enter to skb recv (It will have tons of information, about source, destination, connection, checksum, packet, connection and Flags to tell what type of packet it is; which will be SYN in our case).
Then packets is queued, and consumed by network hardware.
Right after the consumption i am transmitting something but what ??
*It is actually the SYN, ACK, and the protocol stack does it without involving the application.*
We can say that due to scheduling we observed the sending of *ACk* amidst the consumption.
Then it goes to polling to see whether something more is left to read, then software interrupt exits. 
Then we raise another interrupt which finally unblocks the server application.
It takes a while for client side to send *ACK*, and on that another round of this happens, which is explained below.


### accept
After the process wakes up and select executes then where is SYN packet ??
This thing is not happening synchronously. Kernel is not acting synchronously, as on an interrupt it handles the recvd packets. To need to look at an interrupt.
Now this is not waking up of the ncat thread but a different thread whose job is to handle interrupts. It is being waked up and being said that "hey an interrupt arrived, wake up".
After the **hardware interrupt** some very basic waking happens then the **software interrupt** is raised to handle rest of the things as we dont want to keep the resources busy for too long with the hardware interrupt.
**Software interrupt**:  It does network recv, then consumes the socket buffer, then network interface goes back to polling mode to check for more packets, then exits the software interrupt.
*During the skb consume it has also copied the packet to the file descriptor for the data socket which was made when the TCP connection was accepted.*

h/wIRQ -> s/wIRO -> it guides and process packet from the network stack -> copied it to the data socket file -> exit.

So, the kernel only bother to unblock the **select** only when the *ACK* comes from the client, as when it recvs the *SYN* then client may not be committed. *So the ncat process is not involved until the Kernel is done with the handshake with client*.

### What happens on the application when you recv the *ACK* ??
Nothing, so it is idle. So, TCP implementation is inside the kernel, which entirely takes care of the ACK.

### sendto
List of events:
* syscall_entry_sendto
* net_dev_queue: this tells me packet being consumed in the network device. It is enabled by net_* in lttng.
* skb_consume: sbk (socket buffer), it is being consume
* net_dev_xmit: transmit
* syscall_exit_sendto
Hence, start -> queue -> consumed by device -> transmit -> exit
Packet capture happens between queue and consumption.

The detailed interrupt which goes to the protocol stack and process the packet handles more than twice at ACK, and at RST also.


### Some interesting facts

```TCP
cat /proc/net/tcp/
```
If you have net connection then you will get the inode number of socket as explained before then use it to reference in output of this given command.

So, I can get the file descriptor number from the processID, then from that I get the Inode number of the sockets then from that if the connection exists then I can get the connection information using the above commands.
