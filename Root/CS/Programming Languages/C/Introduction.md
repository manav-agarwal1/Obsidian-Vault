- General Purpose Programming Language
- Generally associated to UNIX but not actually associated with any OS
- Low Level Programming Language - Used to write lots of numerical, text processing and data-base programs.
- Deals with most objects that computers do - characters, numbers and addresses.
- No operations to deal with composite objects such as *strings, sets, lists or arrays*.
- Language does not define any storage allocation facility other than static definition and stack discipline provided by local variables of the numbers.
- No heap or garbage collection.
- C itself provides no I/O: no Read or Write or Wired-in files access methods. Write functions for it.

***
- Lack of heap and garbage collection is good and bad.
	- simple *malloc* and *free* functions are there to request certain dynamic memory or free it.
	- Heap: it refers to this dynamic memory that we borrow and return later.
	- If we don't *free* borrowed memory then we have created a **memory leak**.
	- Modern languages don't need this as they automatically clear unused dynamic memory.
	- Though after series of calls to *malloc* and *free* the heap space becomes fragmented and some cleanup is needed, this cleanup is called **garbage collection**.
		- It is tricky so, it was left out of C and left for run-time library.
***

- C offers *single thread control flow instructions*: [[Tests]], [[Loops]], [[Grouping]] and [[Subprograms,]] but not [[Multiprogramming]], [[Parallel Operations]], [[Synchronization]] or [[Coroutines]].
- Though it miss out on these things, it is very small and simple, and compilers for it are can be written easily for most current machines without reinventing the curve.
- As, it is reflecting capabilities of current computers, there is no need to write Assembly. *Eg:* UNIX which is mostly written in C with a very small portion of Assembly. All UNIX applications are written in C.
- This approach of leaving out the more programmer specific requirements out of C and for run-time libraries C has expanded very much without needing revisions to core language or compilers.
- C matches capability of many computers, but *independent of particular machine architecture.*
- BCPL and B is the history before C, those were typeless languages and only data type there was machine word. Other objects were accessed either by custom operators or functions.
- In C fundamental data types are: *characters, integers(variable sizes), float*. In addition derived data types created using *pointers, arrays, structures, unions and functions.*
- Fundamental Flow Control constructions is there in C: *statement grouping, if, while, for, do, switch*.
- C has **pointers** and ability to do **address arithmetic**.
- Arguments of functions are passed by copying the value of arguments, and it is impossible for called function to change actual argument in the called. For *call for reference*, we need to explicitly pass the pointer. Array named are passed as *location of array origin*, so call by reference.
- Functions can be called *recursively*, and its local variables are *automatics* -> created at invocation.
- Function definitions cannot be nested but variables can be declared in a block.
- Functions can be compiled Separately, but variables internal or external need to be in single source file or completely global. Internal variables may be *automatic* or *static*.
- *Automatic variables* can be placed in registers for efficiency but that declaration is hint to C compiler and not actual machine register.
- C is not strongly types like Pascal or Algol68 and has some data conversion but won't convert with abandon of [[PL/1]]
- Existing compilers provide no run-time check. For strong type checking we use **lint**. It has strict checking for ![[Pasted image 20231219141328.png]]
- Separating check to **lint** makes C easy to port. Modern [[Lint]] are more strict then [[Compilers]], and use more memory and resources.
***
*This building of two programs to specialize in one task is called [[Separation of Concern]], it is important principle in Computer Science.*
***
