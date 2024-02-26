Continuing stack Implementation in [[Lecture 5]].
We will try to going to do a generic stack.
# Stack.h
```stack.h
typedef struct {
	void *elemms;
	int elemSize;
	int logLen;
	int allocLen;
	??
} stack;

void StackNew (stack *s, int elemSize);
void StackDispose (stack *s);
void StackPush (stack *s, void *elemAddr);
void StackPop (stack *s, void *elemAddr); // elemAddr to catch poped element
```

# Stack.c
```StackNew
void StackNew (stack *s, int elemSize) {
	assert (s->elemSize > 0);
	s->elemSize = elemSize;
	s->logLen = 0;
	s->allocLen = 4;
	s->elems = malloc ((s->allocLen)*elemSize);
	assert(s->elems != NULL);
}
```
```StackDispose
void StackDispose (stack *s) {
	// Need to something extra in case I have pointer arrays or structs
	free (s->elems);
}
```
```StackPush
static void StackGrow (stack *s) {
	// static means here: it is a private function which should not be advertised outside this file, it cannot be called by other files.
	// this information is only about plain functions in C, not about methods of class.
	s->allocLen *= 2;
	s->elems = realloc (s->elems, (s->allocLen)*(s->elemSize))
}
void StackPush (stack *s, void *elemAddr) {
	if (s->logLen == s->allocLen) {
		StackGrow (s); // Takes care of reallocation
	}
	void *target = (char *) s->elems + (s->logLen)*(s->elemSize);
	memcpy (target, elemAddr, s->elemSize);
	s->logLen++;
}
```
```StackPop
void StackPop (stack *s, void *elemAddr) {
	assert (s->logLen > 0);
	s->logLen--;
	void *source = (char *)s->elems + (s->logLen)*(s->elemSize); // we have already done a -1
	memcpy(elemAddr, source, s->elemAddr);
}
```
