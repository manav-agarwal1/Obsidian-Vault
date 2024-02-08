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
