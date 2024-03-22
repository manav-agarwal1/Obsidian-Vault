We use stack from [[Lecture 6]]
```Eg
int main (_, _) {
	const char *friends = {"AI", "Bob", "Carl"};
	stack stringStack;
	StackNew(&stringStack, sizeof(char *));
	for (int i = 0; i < 3; i++) {
		char *copy = strdup(friends[i]);
		StackPush(&stringStack, &copy); // it replicates whatever there is in copy that is pointing to string, and save it in stack;
	}
}
```