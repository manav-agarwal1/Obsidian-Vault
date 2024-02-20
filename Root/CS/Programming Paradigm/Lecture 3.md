# Structs
- Always $8$ bytes, it stores the address pointing to the first field in `struct` and post that we have other fields with relevant offset based on the data-types.
```swap
void swap (int *ap, int *bp) {
	int temp = *ap;
	*ap = *bp;
	*bp = temp;
}
```
- `array = &array[0]`
- `array + k = &array[k]`
- `*array = array[0]`
- `*(array+k) = array[k]` // compiler knows that it is `k*4` bytes offset when we set to int. But not in case of `void*`.
***
# [The UNIX programming environment](https://see.stanford.edu/materials/icsppcs107/08-Unix-Development.pdf)
- Tools are separate entity.
	- Editor
	- Compiler
		- *Source file must be compiled into **object modules***, it contains a system dependent, relocatable representation of the program in source file.
	- Linker
		- **Object modules** are linked together to produce a single executable file which the system loader can use when the program is actually invoked.
	- make
		- Makefile consists of series of `make` variable definitions and dependency rules. Variables are like macros.
		- Try to keep all variables name capital.
			- `CC` = name of C compiler.
			- `CFLAGS` = List of options to pass on to C compilers.
			- `LDFLAGS` = List of options to be passed to linker
		- Dependency rules = tell how to make target when certain components are changed.
			- Ordering of rules doesnt matter, except first rule is default rule and it is called when make is called without arguments.
			- $2$ lines
				- First to tell which file depend on what
				- Second line should be `tab` indented and it tells the command to be used for make
	- debugger
- `g++`
	- `-c` = source file directly to object stage without linking stage. Important for compiling only those files that changes instead of the project.
	- `-o <file?` = suggests compiler output to be named file. Can be used to customize name in both compiling and linking, but generally used for executable.
	- `-g` = directs compiler to use debugging option.
	- `-Wall` = Give warnings about dubious constructs which are syntactically correct. It is primitive *style checking*.
	- `-I<dir?` = Adds directory to search for include files.
	- `-l<lib>` = search library `lib` for unresolved names during linking. Position of `-l` will make difference. Linker doesn't go back to look for unresolved names. So, if we have a library using `math` then it must appear before `math`.
	- `-L<lib>` = adds directory to be searched for libraries.