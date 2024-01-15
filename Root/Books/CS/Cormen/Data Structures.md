# Stack
```
const int N = 2'000'000;
int st[N];
// top is the location of previous element, so, it starts as invalid position which is -1
int top = -1;
bool is_empty () {
	return top == -1;
}
bool push (int x) {
	top++;
	if (top == N) {
		cout << "Memory Full \n";
		return false; // Error
	}
	st[top] = x;
	return true;
}
bool pop () {
	if(!is_empty()) {
		return st[top--];
	}
	cout << "Stack Empty \n";
	return false;
}
```
***
# Queue
```
const int N = 2'000'000;
int qu[N];
// tail means position where we enter the element;
int tail = 0;
// head means the position of element to pop;
int head = 0;
bool is_empty () {
	return tail == head;
}
bool enqueue (int x) {
	qu[tail] == x;
	tail++;
	if (tail == N) {
		// wrap
		tail = 0;
	}
	return true;
}
bool dequeue () {
	if (is_empty()) {
		cout << "Queue Empty \n";
		return false;
	}
	int res = qu[head];
	head++;
	if (head == N) {
		// wrap
		head = 0;
	}
	return x;
}
```
***
# Linked List
