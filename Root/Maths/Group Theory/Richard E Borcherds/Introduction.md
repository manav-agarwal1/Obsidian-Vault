**What is a Group?**
*Group* is collection of Symmetries of an object. 
**Symmetry** = Mapping something onto itself preserving the structure.

*We are going to look at some important examples, which will help us understand complex groups better which is done in [[Representation Theory]]*.
*Eg:* How many symmetries does a *dodecahedron* has?
**Ans:** Keep one face fixed on a plane, then you $5$ possible symmetries when I do **rotations**. It has $12$ faces, so, in total we have $5*12 = 60$, rotational symmetries. 
Similarly, if we look at **reflection** in same way we get $60$ reflective symmetries. So, in total we have $120$ symmetries for a dodecahedron.

*Eg:* *Cube and Octahedron have same number of symmetries*. *Icosahedron and dodecahedron have same number of symmetries*.
This is not a coincidence, actually these pair belong to same symmetry groups.

*Eg:* ![[Pasted image 20231215183708.png]]
*This star can be rotated by $\frac{1}{5}$*, and it *cyclic*, as it can be thought of as rotating a circle at fifth rotations each time. **Order=5**.

*Eg:* $\mathbf{Z}$, we can only get a symmetry if we shift the points by something, so, we get a group of $\mathbf{Z}$ under addition.![[Pasted image 20231215184037.png]]

*Eg:* **Rubik's Cube**: Has many symmetries.

*Eg:* ![[Pasted image 20231215184207.png]]
Group of symmetries will be a **set of bijection -> map one point to another.** How many?
**Ans:**  $6*5*4*3*2*1 = 6! = 720$. This is called **Symmetric Group ($S_n$)** and here we have $S_6$.

*Eg:* Symmetries of a vector space.
Say, we are in $\mathbf{R}^3$ and set of invertible matrices (determinant $\neq$ 0), forms a group, called $GL_3(\mathbb{R})$. Where $GL$ stands for **General Linear Group**.

*Eg:* Another example come from [[Galois Theory]].
*Group of complex numbers under complex conjugate*, which is called **Galois Group of $\mathbb{C/R}$.**
In Physics, spacetime is 4th dimensional, and we can figure out group of its symmetries. [[Lorentz Group]] and [[Poincare Group]], where you *Fix point* and *Don't fix point* respectively. So, [[Special Relativity]] is study of these two groups.
Similarly we have [[SU_3]] (set of $3\times3$ unitary matrices($A^T A = \mathbf{I}$)) which is important to study [[Quantum Chromodynamics]].
***
# Symmetries of Group

Group is collection of symmetries of an object and we can even look at symmetries of a group.

*Eg:* Take $\text{Symmetric Group of order 5: } S_5 \cong \mathbb{Z}/5\mathbb{Z} = \{0, 1, 2, 3, 4 \,|\, \text{mod } 5\}$
1+1 -> 2, 2+2 -> 4, 4+4 ->3, 3+3 ->1.....So, this will turn out to be 4 symmetries of $S_5$, and it will be a *Cyclic Group.* And, we can iterate this chain of taking symmetries.
***
# Group Axioms
*Anything with this is a group - [[Cayley's Theorem]]*
1. Group is a set with some multiplication (Composition of Symmetries).
2. Identity Element = Trivial Symmetry
3. Associativity
4. Any Symmetry as Inverse symmetry
5. Closure
![[Pasted image 20231215193355.png]]
***
# Goal of Group Theory

1. Classify all groups up to [[Maths/Group Theory/Richard E Borcherds/Homomorphisms|Isomorphisms]].
	-  Sometimes two groups are "Really Same"
	- If we have a function $f: G \to H$ such that,
		- $f$ is a bijection
		- $f$ preserves the *Group Structure*
			- $f(e_G) = f(e_H)$
			- $f(a_G *b_G) = f(a_G) f(b_G)$
			- $f(a_G^{-1}) = f(a_G)^{-1}$
		- Then we say $f$ is an **isomorphism**.
2. Classify all ways "group" is symmetries of something, this is called [[Representation Theory]]. We want to find all ways in which a group can act onto something.
	- *Permutation Representation* = We can either group act on a set
	- *Linear Representation* = We can let group act on a vector space














