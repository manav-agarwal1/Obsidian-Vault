Group is collection of symmetries and this theorem provides us the abstraction to write it with our mathematical machinery.

*This theorem tells us that if we have a group satisfying all the abstract properties then it is in fact symmetries of an object.*![[Pasted image 20231216152232.png]]

***
**Notations**
- $g(s)$ -> $g$ acts on $s$
- $gs$ -> group multiplication

**Group $G$ acts on a set $S$** means we are given a functions $f: G\times S \to S$ (Left action of $G$ on $S$):
- let, $g \in G$, and $s \in S$, then they are mapped to $g(s)$ by $f$, that is action of $g$ on $s$.
- $1_gs = s$
- $g(hs) = (gh)s$, where $\{g, h\} \in G$, and $s \in S$
	- This looks very much like associativity, only $s$ is not in $G$ but in $S$.
	- So, there is an obvious action of $G$ on itself.
		- $g(s) = gs$
	- $G$ is the subgroup of the permutations of $S$.
		- Because, anything we do from $G$ to $S$ it will eventually result in something that is a permutation of $S$.
Here $G$ is symmetries of $S$.

*Eg:* $G$ = symmetries of Octahedron ($24$ elements)
$S$ = 6 vertices of the Octahedron ($6$ elements)
Then map is the action of symmetries on one of the $6$ vertices.

![[Pasted image 20231216160046.png]]

**This is a weaker version of Caley's Theorem** because it says some group is subset of permutation of a set. But we still haven't confirmed that if we have a group then it is indeed group of symmetries of a mathematical object.

To arrive at the **stronger version** we need to add some more structure.

**Right action of $G$ on $S$** = There is a function $f: S \times G \to S$ such that,
- let, $g \in G$, and $s \in S$, then they are mapped to $(s)g$ by $f$, that is action of $g$ on $s$.
- $(s) (gh) = ((s)g) h$, where $\{g, h\} \in G$, and $s \in S$
- $(s)1_g=s$
- Right action is not necessarily same as left action
	- But when $sg = gs$, then we say $S$, $G$ commute.
	- $G$ is then called **Abelian**.
	- But not all groups are **Abelian**.
		- *Eg:*  ![[Pasted image 20231216161029.png]]
		- Two types of symmetries: *blue* are reflective, and *red* are rotatory.
			- $A = (12)$ meaning $1 \to 2, 2 \to 1$
			- $B = (123)$ meaning $1 \to 2, 2 \to 3, 3 \to 1$
			- $AB = (23)$ meaning first do $B$ then $A$.
			- $BA = (13)$, as at the end $1 \to 3$ and $3 \to 1$.
			- So, not **Abelian**.
***
**$G$ acting on the left preserves the right action**
$g(sh) = (gs)h$, where where $\{g, h\} \in G$, and $s \in S$. This is just **Associativity**. So, $gs$ doesn't have to commute but $\{g, h\} \in G$ acting on $s \in S$, their actions preserves each other and hence, these actions can commute.
***
Now, we can treat $G$ = All Symmetries of the object *($S$ which is $G$ but we forget that it is a group)* with structure *(Right action of $G$ on $S$)*.
When we talk about symmetries we mean *Left action of $G$*
**This is CONFUSING**

**Prove that** if $\exists f$ as a symmetry of $S$ which preserves the *Right action of $G$ on $S$*, then $f \in G$.
**Proof**: $$f(s) = f(1s) = f(1)s$$
So, $f$ is just $f(1) \in G$. So, any symmetry of $G$ with its right action is element of $G$. So, any symmetry of $G$ along with its right action is element of $G$.

**Caution** $G$ doesn't preserve group action on $S$. That would be saying g(ab) = (ga)(gb) which is not always true. That would be special case of [[Homomorphisms]].

**Result:**
**So, $G$ doesn't preserve the structure of $S$, but it preserves the Right action of $G$ on $S$**.
***
# Cayley Graph

*Eg:* $G$ = Symmetries of a rectangle ($4$ symmetries) = $\{e, \text{Flip around horizontal axis}, \text{Flip around vertical axis}, 180\degree\text{ rotation}\}$
![[Pasted image 20231217013914.png]]
So, we have each color corresponding to one element of the group. ![[Pasted image 20231217014051.png]] This shows what happen when we multiply each element by the element depicted by color from the right. This is called the **Caley Graph** (*Group together with right action*).
$G$ = symmetries of this graph
By symmetries we mean a *Bijection* of vertices, such that every colored line in this graph is mapped to another colored lined with same arrow direction.
Though above case is simple as $G$ is **Abelian**.


*Eg:* $G$ = Group of symmetries of a triangle = $\{e, (12), (23), (17), (123), (132)\}$
These are reflective and rotational symmetries of a triangle.
![[Pasted image 20231217014941.png]]Different colors for each group element.![[Pasted image 20231217015342.png]] This is what is happening ![[Pasted image 20231217015419.png]]
$G$'s $6$ elements is the group of automorphism of this messy figure, it is not automorphism of triangle, but this messy figure.
***
# 8 actions of G on S(=G)
- Left : $g(s) = ?$
	- Trivial: $g(s) = s$
	- Left Translation: $g(s) = gs$
	- $g(s) = sg^{-1}$
	- Adjoint: $g(s) = gsg^{-1}$
- Right : $(s)g = ?$
	- Trivial: $(s)g = s$
	- Right Translation: $(s)g = sg$
	- $(s)g = g^{-1}s$
	- Adjoint: $(s)g = g^{-1}sg$

*Q.* Why can't $g(s) = sg$?
*Ans:* Say it is true,
then $(gh)s = s(gh)$
but taking $LHS$, 
$$
\begin{align*}
& (gh)s &&=g(hs), &&\tag{Associativity} \\
& &&=(hs)g, &&\tag{Assumption} \\
& &&=(sh)g = s(hg), &&\tag{Assumption} \\
& &&\neq s(gh), &&\tag{If G is not Abelian} \\
\end{align*}
$$
So, by contradiction our assumption is wrong.

*Q.* Why can't $g(s) = sg$?
*Ans:* Say it is true,
then $(gh)s = s(gh)$
but taking $LHS$, 
$$
\begin{align*}
& (gh)s &&=g(hs), &&\tag{Associativity} \\
& &&=(hs)g, &&\tag{Assumption} \\
& &&=(sh)g = s(hg), &&\tag{Assumption} \\
& &&\neq s(gh), &&\tag{If G is not Abelian} \\
\end{align*}
$$
So, by contradiction our assumption is wrong.

Similarly, we can prove if we have doubts about why other variants are not here.
***
# Summary

- Axioms of the group capture the concept of symmetries of object.







