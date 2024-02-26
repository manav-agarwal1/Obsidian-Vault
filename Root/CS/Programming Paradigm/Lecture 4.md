We wrote `swap()` in [[Lecture 3]], and there we expect it to be `int *`.
But now we want a *generic* type and for that we will use `void *`.
```swap_gen
void swap (void *vp1, void *vp2, int size) {
	// vp1 and vp2 store something that begin at address stored by them
	// I have no information about length of that data.
	// So naturally if I dont know how many bytes to read from address then I cannot dereference (void *)
	// size = Number of bytes making data stored. Just number of bytes no data type dependence
	
	char buffer[size]; // just using char as it is 1 byte
	memcpy(buffer, vp1, size); // as buffer is just the address of first byte so, it is a pointer is you just write buffer
	memcpy(vp1, vp2, size);
	memcpy(vp2, buffer, size);
}
```
- 
```
int x = 4;
int y = 17;
swap(&x, &y, sizeof(int));
```
- In `C++` we use `templates`. Biggest advantage of *generic pointers* is that same code is compiled for above `swap` and same assembly code is used for all the data-types.
	- But in `templates`, in extends to `swap of int` or `swap of double`. That is problematic when we call `swap` in a very large codebase, there we get multiple copies of, one for each data-type. So, this `C` version can serve us better there.
	- Though this `C` version is `error prone`, as say you pass `float` and `double` and `32`, it will run in `C`, though that wont look very good.
		- Say,
```
		int i = 44;
		short s = 5;
		swap(&i, &s, sizeof(short));
```
		This will not work well in **big endian** system, because it will change MSB 0 with 5 and vice versa.
		So, $i = 2^16 *5 + 44$
		But it will survive compilation.
		Though it will work fine with** little endian** system.
***
```
char *h = strdup("FRED");
char *w = strdup("WELMA");
// I get FRED\0 in heap and WELMA\0 in heap and these point to those.
// Swap?
swap(&h, &w, sizeof(char *));
// we swap the vp1 and vp2 that point to h and w.
// So, we forget about data in heap. It just changes pointer in h and w
// So, we provide sizeof(char *)
```
If we forget something and do `swap(h, w, sizeof(char *));` it will still run, it won't crash but the result will be weird. `sizeof(char *) = 4bytes`. It exchanges $4$ bytes from the data in heap. The result will be `h = WELM`, and `w = FREDA`
***
```
void* lsearch (void* key, void* base, int n, int elem_size) {
	for (int i = 0; i < n; i++) {
		// void* elem_address = base + i*elem_size; this wont work as base is void* and compiler just wont budge
		
		// hack: used everyday in generic C programming
		void* elem_address = (char*) base + i*elem_size;
		// just bare memory compare, not gonna work for structs though as they have pointers not the data
		if (memcmp(key, elem_address, elem_size) == 0)
			return elem_address;
	}
	
	return -1;
}
```
```


