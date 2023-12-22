---
(OS) Operating Systems: Kernel, Linux, Windows
Author: "\rMark Russinovich"
---
#CS
# Introduction

***Kernel***: Designed to manage the resources of the computer as efficiently as possible so, the applications can perform as efficiently possible. In order to classify a *kernel* as good or bad, you have to talk about how applications can utilize the *kernel services* to do what they want to do. One way to measure that is through benchmarks.
The two OS are very similar from a kernel perspectives as they were born around the same time.
### Linux
- 1969, Ken Thompson developed the first version of UNIX in Bell Labs.
- Dennis Ritchie co-authored a paper in 1974 with Ken on UNIX. [*Paper Link*](https://dsf.berkeley.edu/cs262/unix.pdf)
- 1976, Bell Labs released first commercial version called #V6.
- 1978, release of UNIX Time-Sharing System.
- Because, Bell Labs distributed UNIX with source code, early 1980's saw three major branches of UNIX tree:
	- UNIX #SystemIII
	- UNIX #BSD
	- Microsoft's #XENIX: It was the biggest UNIX vendor, at that time.
- Due to this diversity IEEE #POSIX standards and #X/Open Group Portability Guide, but market fragmented further.
- 1991, Linus in a course found #Minix and wanted to make it more usable, but author said keep it simple. So, he went ahead and released Linux v0.02 later that released, and in 1994, released #Linux v1.0
### Windows
- In 1970s, Dick Hustvedt, Peter Lipman and David Cutler designed VMS OS to target Digital's 32-bit VAX processor
- Bill invited Culter after his project cancellation from Digital, and hired  couple people from Digital and started to work on NT OS/2.
- In 1990, release of Windows 3.0, first successful version of 16 Bit windows OS.
- In 1993, release of Windows NT 3.1.

# Architecture
- Both *Linux* and *Windows* are **monolithic** ie; all core OS services run in the same address space in kernel mode. Almost all commercial OS have monolithic kernel for performance advantage.
- All core OS services are part of same module:
	- **Linux** = vmlinux
	- **Windows** = ntoskrnl.exe 
- Windowing is handled differently:
	- **Windows** = kernel mode windowing subsystem.
	- **Linux** = user mode X-windowing system
### Linux
![[Pasted image 20231121172123.png]]
Message sent to X-Window process which is like any other user mode process.
- Can degrade performance, but there are some ways it handles.
- It makes it very easy to remote an application. We can just have the window of the app on another machine and app can run on another machine.
### Windows
![[Pasted image 20231121172317.png]]
No message just simple transition from user to kernel space.
- No message so no performance drop.
- You cant remote an application. Eg. You cant run Word on another machine and see the window coming on another. You have to get a terminal server and a whole desktop.

# Process Management
###  Linux
- **Task**: It has a basic address space, handle table, statistics.
- Inherent parent/child relationship.
- Basic Scheduling unit.
- No such thing as a thread, a task can look like a windows thread or process by sharing handle table, PID and address space.
- We create tasks with a system call *clone* where we can say what aspects of this new tasks we want to share with the old task. Windows NT equivalent of process will share nothing, but for thread everything.
- P-threads = cooperative user mode threads.
- *Scheduler*: Low are favoured
	- Scheduling classes: 
		- *Normal* = 100-139, Dynamic, so priority can decay (ie; grow up).
		- Fixed RR = 0-100
		- Fixed FIFO = 0-100
	- Priority of interactive tasks go down (boost) to give them more chance of CPU execution.
	- And thread that consumes CPU will have priority decay.
	- Reentrant
	- Preemptible
### Windows NT
- ***Process***: Basically a container, that has a address space (code and data live here), handle table (what OS resources process is using), statistics and has at least one thread.
- No inherent Parent/Child relationship between processes. When a process creates another process the creator gets the identifier of the process but wont be alerted when the child dies until subscribed to it, and when parent dies nothing happens to the child.
- *Thread* is the basic scheduling unit on windows.
- *Scheduler* priority classes: High are favored.
	- Two priority classes:
		- *Real time* (fixed)= 16-31, scheduler will not modify the priority.
		- *Dynamic* = 1-15, scheduler can manipulate the priority based on thread's actions. One way is boost priorities of thread of more I/O to give them the chance to wake up and execute in the CPU.
	- A thread's priority will never decay below its original priority.
	- Preemptible
	- Reentrant

# Scheduling
### Linux
- Time quantum is 10-200 ms.
	- Default quantum is 100ms.
	- Varies across based on priority which is determined by interactivity.
- Support SMP
	- No upper limit on CPU number. It is a compile time number, set as Kernel build constant.
	- All CPUs can take interrupt.
- Support for NUMA
	- Scheduler is NUMA aware #numa_aware.
	- Memory manager is not NUMA aware as windows NT.
- Support Hyperthreading same as windows.
### Windows
- Time quantum is 10ms - 120ms. Can have all that all threads have same quanta or have that foreground threads have more quanta than the background threads.
- Support symmetric multiprocessing (SMP)
	- upto 32 processors on 32-bit windows.
	- upto 64 processors on 64-bit windows.
	- all CPUs can take interrupts.
	- all CPUs have access to the physical memory present on the machine.
- A variant of SMP ie; NUMA is also supported by windows NT. In NUMA we have nodes of processors and each node will have a local block of memory and it is shared by processors in that node. Processors can still talk to other processors on the remote node but it takes longer time to talk to a remote processor.
	- Scheduler favors the node on which thread prefers to run on. #numa_aware
	- Memory manager also tries to allocate memory on the same node #numa_aware.
- Windows system support hyperthreading. It is the case where one physical processor looks like two to the scheduler. 
	  *Imagine having 2 physical processors with 2 logical ones on each, so 4 logical processor on each. If one thread of processor 1 is running on 1st logical processor then when task come a hyperthreading aware CPU will schedule it on the logical processor on the second physical CPU*
	- Favor idle physical CPU.
	- Doesn't count logical CPU against licensing limit.
	  
# Memory Management
*Virtual memory management and Physical memory management*
### Linux
- user-mode: 1-3GB; kernel-mode:1-3GB.
- linux 2.6 has 4/4 split option, where kernel has its separate address space, where we need to do complete remapping when going from user to kernel space and it is done for memory intensive applications like databases.
- Demand-paged virtual memory
	- 32 and/or 64-bit
	- Copy on write
	- shared memory
	- Memory mapped files: where can map file address in to address space and manipulate everything as if it is a buffer.
- Physical memory: big difference from windows
	- There is a global working set.
	- No cap on process
	- It is a global working set and stealing of old page happens from any global page instead of application local pages
	- working set trimmer code that steal pages from working set to replace is called swap #daemon
- No swapper
### Windows
- On 32-bit systems (4 GB address space), manager splits the address space into half where the lower halves are for the user space, and upper half is for system (ntoskernel.exe, drivers, buffers and data). Done for ease of communication can be done easily between user and system by doing memcopy up and down above 2GB line without switching address spaces.
- Demand-paged virtual memory:
	- 32 and/or 64-bit
	- Copy on write
	- shared memory
	- Memory mapped files: where can map file address in to address space and manipulate everything as if it is a buffer.
- Physical memory: Each process is assigned a working set which grows and grows until manager says that this process has enough physical memory and I am going to cap it now. and if process need some data that is not part of working set than memory manages steals something out of it and replaces it with required working set. Does that using #clock algorithm. Steals aged working set with the hopes it wont be needed in the futures.
- No swapper
- Can boot windows NT with user memory having 3GB and kernel with 1GB address space, so support virtual memory intensive applications like SQL, so they can map more user space.

# I/O
### Linux
- Centered around the data structure called **inode**.
- No layered I/O model: Mark Russinowich (CTO Azure), thinks it is a deficiency.
- I/O synchronous
	- Only sockets and direct disk I/O support asynchronous I/O. (as database application like Oracle perform these).
- IRQL controls interrupts.
- Interrupts are spit between #hard_interrupts and #soft_interrupts
- Supports plug and play
### Windows
- Centered around a memory object called *filed object*.
- *Layered Driver architecture*: Gives the ability to write the drivers that inserts over another driver no matter who wrote them, so we can modify driver behavior. Eg. on access virus scanner: they insert driver over the file system that watches the file for access and on open request from any application it intercepts it and scans the application for virus and quarantines if threat.
- Most of the I/O support asynchronous operation: lets application manage their I/O effectively with threads they create. Without it threads will have to wait a lot.
- Internal interrupt request level (IRQL) controls interruptability.
	- Interrupts triggers a #ISR: Simply gets some state with device and tell OS to call back when interrupts are enabled, as we dont want interrupts to be off for a long time, after telling what it wants to do.
	- Deferred Procedure Call (#DPC): the main chunk.
- Supports plug and play.

# File Caching
### Linux and Windows
- Single global common cache.
- #Virtual_Cache 
	- Caching is by file offset and length into file instead of block level cache (cache based on sectors they occupy on the disk).
	- Lots of advantages to having a virtual cache.
	- Files are memory mapped into kernel memory.
- Supports *zero copy file sending*, where someone can take a piece of a file that's been mapped into the cache hand it to network driver and say "send it out", and network driver will send it out without making copies of it at any point of the time (in memory).
  
# Security
### Linux
- Two models:
	- **Access Control Lists** (*SELinux*: with v2.6 add-on)
	- **Standard UNIX model**
- Users are defined with:
	- Capabilities (privileges)
	- Member groups
- Security is implemented **Object-by-object** basis.
- No built-in auditing support
- v2.6 included Linux Security model framework for add-on security models.
### Windows NT
- Flexible security model based on **Access Control Lists**.
- Users are defined with:
	- Privileges
	- Member groups
- Security can be applied to any *Object Manager* object
	- Files, processes, synchronization objects,...
- Supports auditing.

# Linux Evolution towards Windows
- **I/O Processing** = 
	- Linux 2.2 had notion of bottom halves for low priority interrupts. Only fixed number of these were allowed and at a time only one could be active (across all CPUs). If you had a device driver you had to register those bottom halves.
	- Linux2.4 introduced *tasklets* which are exact equivalent of windows *DPC*. Non preemptible from scheduler perspective.
- **Kernel Reentrancy** = 
 ![[Pasted image 20231122000318.png]]
	- Dark Yellow: waiting for kernel, Yellow = Kernel mode
	- Linux2.2 was reentrant.
	- **Reentrant** : multiple processes can execute system calls in kernel.
	- Ingo Molnar made all the major paths reentrant.
- **Kernel Preemptible** = 
	- Preemptible kernel is more responsible to high priority tasks.
	- Linux2.4 was only *cooperatively preemptible* (there are well defined safe places where a thread running in the kernel can be preempted, but the tasks has to yield it).
	- In patched v2.4 and Linux v2.6 we had preemptible kernel.
	- Windows NT has always been preemptible.
- **Pre-CPU Memory Allocation** = 
	- We want threads to use the cache on the processor they are running on. Have memory manager allocate buffers that can be accessed on a particular CPU.
	- Linux v2.4 introduced per-CPU kernel memory buffers.
	- Windows NT introduces these 2 years before in 1997 in NT4 service pack.
- **Scheduling** = 
	- Linux v2.4 scheduler is O(n).
		- So, scan everyone and long duration under the scheduler lock.
	- Ingo Molnar gave a O(1) scheduler in patch of v2.4
		- Calculate tasks' priority at the times it make scheduling decision.
		- Per-CPU queue ready where the tasks are pre-sorted by priority.
	- Windows NT has been always O(1) based on pre-sorted thread queues.
	- Sever 2003 introduces per-CPU ready queue.
		- Linux load balances queues whereas Windows doesn't.
- **Zero-Copy Sendfile** = 
	- Linux2.2 introduced an API that claimed to do this, but it did one copy from the cache into a buffer before it is consumed by the network driver.
	- Linux2.4 introduced the zero copy.
	- Windows NT pioneered this with TransmitFile, introduced in Windows NT 4.
	- This is important for scaling web servers.
- **Wake-one Socket Semantics** = 
	- Linux2.2 has #thundering_herd or #overscheduling problem
		- this happens on client-server application where several threads wait for a connection request from a client. When request comes in network socket then all threads wake up to claim it then one of them wakes up and all gets back to sleep. This is surge of activity that scheduler has to take care of and hurts performance.
		- Ingo Monar fixed it in 1999.
	- From Linux2.4 only one thread wakes up to get the new connection.
	- Windows NT has always been wake-1 semantics.
- **Asynchronous I/O** #AIO = 
	- Linux2.2 only supported asynchronous I/O on socket connect operations and tty's.
	- Linux2.6 adds asynchronous I/O for direct-disk access.
		- AIO model includes efficient management of asynchronous I/O. So, threads can issue multiple I/Os and wait for them if they want to.
			- Add alternate epoll model
		- Useful for database servers managing their database on a dedicated raw partition.
		- Database servers that manage a file-based database suffer from synchronous I/O
	- Windows was inherently asynchronous.
	- Windows had **completion ports** since NT 3.5
		- More advanced for of AIO = tried to throttle number of threads active on a particular CPU, as in enterprise we want only one thread running on CPU and other threads waiting for workload, it is achieved by completion ports using hooks into the scheduler.
- **Light-Weight Synchronization** = 
	- Linux2.6 introduces Futexes (Fast Mutexes)
		- There is transition to kernel mode when there is a contention to decide who gets to execute. Otherwise, if no contention then no transition to kernel mode, threads come modify and go.
	- Windows always had CriticalSections
		- Same thing as Linux
		- Only work within same process.
	- Futexes go further than Windows CriticalSection:
		- Allow for prioritization of waits.
		- Works interprocess as well.

