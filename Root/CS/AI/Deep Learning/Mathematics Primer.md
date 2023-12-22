---
Maths:
---
- *Convention:* All vectors are by default column, if transpose sign then it is row.
- **Set**, **Scalars**, **Vectors**, **Matrices** are trivial.

- **Tensor**: Arrays are with more than 2 axes (ie; RGB).

- **Matrix Hadamard Product**: Element wise products of individual elements.
- ![[Pasted image 20231130123801.png]]
- **Inner Product**: $A$ and $B$ are two column vectors. Inner product = $A^TB$ 
- **Outer Product**: $A$ and $B$ are two column vectors. Inner product = $AB^T$. Matrix of Rank 1.
![[Pasted image 20231130124043.png]]
![[Pasted image 20231130124209.png]]
![[Pasted image 20231130124329.png]]
![[Pasted image 20231130124449.png]]
- **Inverse**: $A^{-1}$ exists only if $A$ is full rank matrix.
- If $Ax = b$ is a linear system we can solve it like with $A^{-1}$ but it is not advisable as it is not stable, due to numerical precision.
- ![[Pasted image 20231204160806.png]]
- **Span:** Set of all points obtained by linear combination. That is we vary x and all possible $b$ is the span of vectors represented by columns of $A$.
	- $Ax = b$ $<=>$ $b$ is in span of $A$.
	- ![[Pasted image 20231204161734.png]]
	- Exactly one solution
- No solution when columns of $A$ are linearly dependent. No matter what you do with $x$ you wont go away from the $A$ line. 
	- ![[Pasted image 20231204161431.png]]
- Infinite solutions when $b$ is also parallel to columns of $A$, so all columns of $A$ and $b$ are linearly dependent.
	- ![[Pasted image 20231204161709.png]]
- ![[Pasted image 20231204161934.png]]
- ![[Pasted image 20231204164929.png]]
- ![[Pasted image 20231204165147.png]]
- ![[Pasted image 20231204165202.png]]
- ![[Pasted image 20231204165633.png]]
- ![[Pasted image 20231204170144.png]]
- ![[Pasted image 20231204170414.png]]
	- ![[Pasted image 20231204170437.png]]
- 