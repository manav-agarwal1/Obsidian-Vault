# Cache

- **Block** = Main unit of data transfer. Typically $64$ bytes in intel core **i7** chip.
- **Cache** holds a small number of blocks which are frequently used **blocks**. **CPU** first ask for data from **cache**, if it doesn't have then it retrieves data from the main memory. **Cache** retrieves data in **blocks** irrespective of amount of data required.
- **CPU** doesn't know about **cache**, it thinks it is talking to the main memory.
- Main memory doesn't know about **cache**, it thinks it is talking to the **CPU**.
***
- **Traditional Memory (Byte Addressable)**: You give address and in return the byte at that address is returned. If address is $N$ bits then we have $2^N$ values stored.
- **Associative Memory**: Data stored as *key*-*value* pair, so, you give *key* and get data. It may come out as not all *key* are present. *Key* can be of any size. Smaller number of lines.
	- For **cache**, we have *Key* as address of the block and *value* is the block data.
	- **Fully Associative Cache**: 
		- Block size $B$, Number of lines $L$, Number of sets S, Address size A
			- Size of the cache C= $B*L$, there can be other bits like Key and dirty bits, but we only talk about block data size here.
			- Say, $B = 64 bytes$, $L = 512$, $S=1$, $A = 32 bits$
				- So, the $B = 64 bytes = 2^6$ so, we need $6$ bits for address of the byte within the block. This is called **Block Offset**.
				- Rest $26 bits$ can be called as the Key or **Tag**.
		- All in Hardware, so it is extremely fast.
			- Extract the **Tag** and **Offset**.
			- Send **Tag** to **Associative Memory**.
				- *If Match*: Retrieve the block, use **offset** to extract the byte and send to CPU.
				- *If no Match*: Select a block to evict (If you want to implement algorithms like **L.R.U**),
					- *If selected block is dirty*: Write back to memory.
				- Send the **Tag** to main memory, and get a block.
				- Update the cache lines for *Key* and *Value*.
				- Extract the desired byte and send to CPU.
***

