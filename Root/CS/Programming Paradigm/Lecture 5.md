### Better version
```
int cmpfn (void* elem1, void* elem2) {
	int* ip1 = elem1;
	int* ip2 = elem2;
	return *ip1 == *ip2;
}
void* lsearch (void* key, void* base, int n, int elem_size, int (*cmpfn)(void*, void*)) {
	// function pointer is passed here
	for (int i = 0; i < n; i++) {
		// void* elem_address = base + i*elem_size; this wont work as base is void* and compiler just wont budge
		
		// hack: used everyday in generic C programming
		void* elem_address = (char*) base + i*elem_size;
		if (cmpfn(key, elem_address) == 0) {
			return elem_address;
		}
	}
	return NULL;
}
```
This will work with all data types even with structs, given we pass appropriate `cmpfn`.
***
```Eg
#include <stdio.h>

int main() {
    char *strings[] = {"string1", "string2", "string3"};
    char **ptr_to_first_element = strings;
    char *ptr_to_first_char = strings[0];

    printf("Address stored in ptr_to_first_element: %p, %s\n ", (void *)ptr_to_first_element, *ptr_to_first_element);
    printf("Address stored in ptr_to_first_char: %s, %p\n", (void *)ptr_to_first_char, &strings[0]);

    return 0;
}
```
```Output
Address stored in ptr_to_first_element: 0x7ffe4cb9f480, string1
Address stored in ptr_to_first_char: string1, 0x7ffe4cb9f480
```

```eg2
#include <stdio.h>

int main() {
    char *strings[] = {"string1", "string2", "string3"};
    char **ptr_to_first_element = strings;
    char *ptr_to_first_char = strings[0];

    printf("Address stored in ptr_to_first_element: %p, %s\n ", (void *)ptr_to_first_element, *ptr_to_first_element);
    printf("Address stored in ptr_to_first_char: %c, %p\n", *ptr_to_first_char, &strings[0]);

    return 0;
}
```
```output
Address stored in ptr_to_first_element: 0x7ffd44f02970, string1
Address stored in ptr_to_first_char: s, 0x7ffd44f02970
```

```eg3
#include <stdio.h>

int main() {
    char *strings[] = {"string1", "string2", "string3"};
    char **ptr_to_first_element = strings;
    char *ptr_to_first_char = strings[0];

    printf("Address stored in ptr_to_first_element: %p, %s\n ", (void *)ptr_to_first_element, *ptr_to_first_element);
    printf("Address stored in ptr_to_first_char: %p, %c\n", (void *)ptr_to_first_char, *ptr_to_first_char);

    return 0;
}
```
```output
Address stored in ptr_to_first_element: 0x7ffd8300d220, string1
 Address stored in ptr_to_first_char: 0x55b3f9e84008, s
```

```eg4
#include <stdio.h>

int main() {
    char* strings[] = {"string1", "string2", "string3"};
    char** ptr_to_first_element = strings;
    char* ptr_to_first_char = strings[0];

    printf("Address stored in ptr_to_first_element: %p, %s\n ", (void *)ptr_to_first_element, *ptr_to_first_element);
    printf("Address stored in ptr_to_first_char: %p, %s\n", (void *)ptr_to_first_char, *ptr_to_first_char);

    return 0;

}
```
```output
Address stored in ptr_to_first_element: 0x7ffcb187bc00, string1
Segmentation fault
```

When you write `*<anything>`, that value at that anything is kept there, now `*` makes us treat that value as a address and brings forth things stored at that address.
So, it matters which address you pass either the `char**` ie; the tail of box end, or string address.
Number of `*` = number of hops to reach data.
- No stars= means that variable will bring data.
- 1 star= variable store address of data....so on.
So, `*data` = 1 hop towards data
and, `data*` = 1 hop away from data
***
```
int str_cmp(void* vp1, void* vp2) {
	char* s1 = *(char**)vp1;
	char* s2 = *(char**)vp2;
	return strcmp(s1, s2);
}

char* notes = {"Ab", "F#", "B", "Gb", "D"};
char* fn = "Eb";
char** found = lsearch(&fn, notes, 5, sizeof(char*), str_cmp); // notes is char**, and array stores char* so sizeof(char*)

```
***
# Stack.h
```stack.h
typedef struct {
	int *elemms;
	int logLen;
	int allocLen;
} stack;

void StackNew (stack *s);
void StackDispose (stack *s);
void StackPush (stack *s, int value);
int StackPop (stack *s);
```
```Usage
stack s;
StackNew (&s);

// some push and pops
StackDispose (&s);
```
# Stack.c
```StackNew
void StackNew (stack *s) {
	s->logLen = 0;
	s->allocLen = 4;
	s->elems = malloc ((s->allocLen)*sizeof(int));
	assert(s->elems != NULL);
}
```
```StackDispose
void StackDispose (stack *s) {
	free (s->elems);
	// Donot do free (s), as it is not allocated during StackNew
}
```
```StackPush
void StackPush(stack *s, int value) {
	if (s->logLen == s->allocLen) {
		// In C++, you need to reallocate for large memory, copy old data and destroy old memory
		// C is more close to exposed memory, so we have a function, that takes memory allocated by malloc and resize it
		s->allocLen *= 2;

		// If it finds block next to memory is empty then resize it and returns same address
		// else calls malloc somewhere else, and copies data, frees old addressm and return new address.
		// When first parameter is NULL then realloc defaults to malloc call
		// realloc also takes care of the interpretation of copied data
		// if it was datatype then we trust it to be same
		// if it is pointer arrays even then the new location interpret it as addresses.
		s->elems = realloc (s->elems, s->allocLen*sizeof(int));
		assert (s->elems != NULL); // if NULL then realloc just leaves old memory untouched
	}
	
	s->elem[s->logLen] = value;
	s->logLen++;
}
```
```StackPop
int StackPop (stack *s) {
	assert (s->logLen > 0);
	s->logLen--;
	return s->elems[s->logLen];
}
```


