```
#include <stdio.h>
main() {
    printf("hello, world\n");
}
```

Every C program must have *main*.
- The braces are analogous to DO-END of PL/1 or begin-end of Algol.
- There is a no CALL statement like Fortran or PL/1.
- Just use function name and parenthesis, and arguments.
- *printf* don't specifies the *\n* automatically, so be careful else you can mess up the terminal output feed.
- In C declare all the variables before use.
- ![[Pasted image 20231219190406.png]]
- Character Counting code 
```#include <stdio.h>

main() /* count characters in input */
{
    double nc;

    for (nc = 0; getchar() != EOF; ++nc)
        ;
    printf("%.0f\n", nc);
}
```
- Line Counting Code
```
#include <stdio.h>

main() /* count lines in input */
{
    int c, nl;

    nl = 0;
    while ((c = getchar()) != EOF)
        if (c == '\n')
            ++nl;
    printf("%d\n", nl);
}
```
- ![[Pasted image 20231219192355.png]]
- Word counting: with the loose definition that a word is any sequence of characters that does not contain a blank, tab or newline. (This is a bare-bones version of the UNIX utility _wc_.)
```
#include <stdio.h>

#define YES 1
#define NO  0

main() /* count lines, words, chars in input */
{
    int c, nl, nw, nc, inword;

    inword = NO;
    nl = nw = nc = 0;
    while ((c = getchar()) != EOF) {
        ++nc;
        if (c == '\n' )
            ++nl;
        if (c == ' ' || c == '\n' || c == '\t' )
            inword = NO;
        else if ( inword == NO ) {
            inword = YES;
            ++nw;
        }
    }
    printf("%d %d %d\n", nl, nw, nc);
}
```
- Assignment has a value and assignment  take from right to left.
- Number of elements in an array declaration must be constant at compile time and size of array cannot be adjusted, this leads to **buffer overflow**, and leads program to write into other data or code compromising the application. This is a security flaw.
	- Python has these types of arrays too called *buffers*. Which are not used unless you write code to talk to low level languages.
	- *dynamic memory allocation* and *linked list*  are used to implement Python's list.
- Function call by value - It was a bit of work to make pass by value work in C. C implements a "*call stack*" where a bit of memory is allocated at each function call and C makes a copy of the values in the calling code to pass them into the called code in a way that the calling code can see the values and change their local copies without affecting the values in the calling code.
- Older function syntax (K&R)
```
int add(a, b)
int a, b;
{
    return a + b;
}
```
- New style after c89
```
int add(int a, int b)
{
    return a + b;
}

```
- In Python, *simple variables like integers and strings are passed by value* while *structured data like dictionaries and lists are passed by reference* (i.e. **the called function can modify its arguments**). We will see this in C as well.
- Main thing is in C, a called function cannot do this modification to its arguments.
- In C, It is possible to arrange for a function to modify a variable in a calling routine. The caller must provide the _address_ of the variable to be set (technically a _pointer_ to the variable), and the called function must declare the argument to be a pointer and reference the actual variable indirectly through it.
- In C, When the name of an array is used as an argument, the value passed to the function is actually the location or address of the beginning of the array. (There is _no_ copying of array elements.) By subscripting this value, the function can access and alter any element of the array.
- get_line(): At the minimum, `get_line` has to return a signal about possible end of file; a more generally useful design would be to return the length of the line, or zero if end of file is encountered. Zero is never a valid line length since every line has at least one character; even a line containing only a newline has length 1
```
#include <stdio.h>

#define MAXLINE 1000 /* maximum input line size */

main() /* find longest line */
{
    int len; /* current line length */
    int max; /* maximum length seen so far */
    char line[MAXLINE]; /* current input line */
    char save[MAXLINE]; /* longest line, saved */

    max = 0;
    while ((len = get_line(line, MAXLINE)) > 0)
        if (len > max) {
            max = len;
            copy(line, save);
        }
    if (max > 0) /* there was a line */
        printf("%s", save);
}

get_line(s, lim) /* get line into s, return length */
char s[];
int lim;
{
    int c, i;

    for (i=0; i<lim-1 && (c=getchar())!=EOF && c!='\n'; ++i)
        s[i] = c;
    if (c == '\n') {
        s[i] = c;
        ++i;
    }
    s[i] = '\0';
    return(i);
}

copy(s1, s2) /* copy s1 to s2; assume s2 big enough */
char s1[], s2[];
{
    int i;

    i = 0;
    while ((s2[i] = s1[i]) != '\0')
        ++i;
}
```
- External variables using *extern*.
```
#include <stdio.h>

#define MAXLINE 1000 /* maximum input line size */

char line[MAXLINE]; /* input line */
char save[MAXLINE]; /* longest line saved here */
int max; /* length of longest line seen so far */

main() /* find longest line; specialized version */
{
    int len;
    extern int max;
    extern char save[];
    max = 0;
    while ((len = get_line()) > 0)
        if (len > max) {
            max = len;
            copy();
        }
    if (max > 0) /* there was a line */
        printf("%s", save);
}

get_line() /* specialized version */
{
    int c, i;
    extern char line[];

    for (i = 0; i < MAXLINE-1
        && (c=getchar()) != EOF && c != '\n'; ++i)
            line[i] = c;
    if (c == '\n') {
        line [i] = c;
        ++i;
    }
    line[i] = '\0';
    return(i);
}

copy() /* specialized version */
{
    int i;
    extern char line[], save[];

    i = 0;
    while ((save[i] = line[i]) != '\0')
        ++i;
}
```
- If external variables are in same source file then no need to use *extern*. But if program spans over multiple source files then we need to use *extern*.
- *Declaration*: Place where nature if variable is stated but no storage is allocated.
- *Definition*: Place where variable is actually created ie; assigned storage.