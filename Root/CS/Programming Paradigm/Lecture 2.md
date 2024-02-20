# Low Level Details
*For now `C/C++` are same languages*
- bool
- char:
	- $1$ byte
- short
	- $2$ bytes
- int
	- $2-4$ bytes, but we will assume it is $4$ bytes
- long
	- $4$ bytes
- float
	- $4$ bytes
- double
	- $8$ bytes

*Eg*. if you do:
```
int i = 5;
float f = i;
cout << f << endl;
```
or vice versa, everytime it has to evaluate the bit pattern in the memory for $i$ then figure out what is the `IEEE` representation for that is and assign.

*Eg*.
```
int i = 37;
float f = *(float *)&i;
```
This evaluates the location of $i$.
- `&i` = type `int *`, raw exposed address of a variable, $4$-bytes
- `float *` = it doesn't cause bits to move around or anything it just makes the computer thing that address is of a float, then once we make them think it is a float point number, we dereference it.
It literally just take `int` representation of $37$ and just use that so, see what `float` will look like.

*Eg*.
```
float f = 7.0;
short s = *(short *) &f;
```

- It will take the first upper $2$ bytes, so sign bit, exp, and some $7$ bits of mantissa.
***
# [C++ STL](https://see.stanford.edu/materials/icsppcs107/03-Introducing-The-STL.pdf)

- `pair` = template struct with $2$ input fields.
```pair
template <class U, class V>
struct pair {
	// Public variables of pair class
	U first;
	V second;
	// constructor
	// const U& first = declares first to be a reference to const object of type U
	// = U() it constructs the default initialized object of type U, if U is a class then it invokes the default constructor
	pair (const U& first = U(), const V& second = V()) :
		first(first), second(second) {}
};
// function template : You cannot define function template inside the struct
template <class U, class V>
pair<U, V> make_pair(const U& first, const V& second);
```
All of the associative containers requires pair to be used to insert data, so this container is simple but very useful.

- `vector` = *type-safe*, sequential container
`#include <vector>`
`using namespace std`;
Implementation:
```vector
template <class T>
class vector {
	public:
		// default constructor
		vector();
		// copy constructor, and by writing const you promise not to make any changes to originalMap
		vector(const vector(T)& originalMap);

		typedef implementation_specific_class_1 iterator;
		typedef implementation_specific_class_2 const_iterator;

		bool empty() const;
		long size() const;
		void clear();

		void push_back(const T& elem);
		void pop_back();

		T& operator[](int i);
		const T& operator[](int i) const;
		iterator insert(iterator where, const T& elem);
		iterator erase(iterator where);

		iterator begin();
		iterator end();
		const_iterator begin() const;
		const_iterator end() const;		
}
```
When argument of  `push_back` is a direct object instead of a pointer it takes a **deep copy** of the object. When you add pointers, it just replicates the pointer and the memory referenced is same.

When you invoke `erase` while traversing it returns the next pointer if it was not called, so we don't need to advance the pointer in the iterations we invoke `erase`.

- `map`
`insert` will make no change to existing key even if you try to.
You would have to `erase` and again `insert` or modify. `insert` takes pair of key-value, it is different from `m[k] = v`. it is like `m.insert(make_pair(k, v))`, return value of `insert` is a `pair`. So, if using insert, we can test using the bool.

`const` iterators are good for read-only access, they respect the `const` nature of whatever they are addressing.
