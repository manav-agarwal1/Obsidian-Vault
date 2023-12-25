- **Order 4**: By [[Langrange's Theorem]], it contains elements of order - $1$, $2$ and $4$.
	- If there is an element of order $4$, then group contains elements $\{1, g, g^2, g^3\}$ so, is **cyclic** and **Isomorphic** to $\mathcal{Z}/4\mathcal{Z}$.
	- For element of order 2, we have $x^2 = 1$ $\forall$ $x \in G$.
		- If this $x^2 = 1$ condition is true then group is **Abelian**.
			- Let, $\{a, b\} \in G$, then $$\begin{align*} &ab &&\in G, \\ &(ab)^2 &&= 1, \\ &ab && =(ab)^{-1}, \\ &ab &&= b^{-1}a^{-1}, \\&ab &&=ba, &&...\text{Since, } a^2 = b^2 = 1  \\\end{align*}$$
			- So, group is **Abelian**.
		- These are $\mathcal{Z}/2\mathcal{Z} \times \mathcal{Z}/2\mathcal{Z}$. (*Elementary Abelian p-Groups*).
	- To, check that these two groups are really different, ie; no mysterious **isomorphism**.
		- *Two Groups are **Isomorphic** if they have exactly same number of elements of each order*. Inverse is not always true, but those cases are rare. So, it is a good way of distinguishing groups.
		- $\mathcal{Z}/4\mathcal{Z}$: $1$ element of order $1$, $2$ element of order $2$ and $1$ element of order $1$.
		- $\mathcal{Z}/2\mathcal{Z} \times \mathcal{Z}/2\mathcal{Z}$ (**Klein $4$-group**; group of symmetries of a rectangle): $1$ element of order $1$, $3$ elements of order $2$.
		- So, there is not **isomorphism**.
	- Subgroups of two group:
		- $\mathcal{Z}/4\mathcal{Z}$:
			- Order $1$
			- Order $2$
				- Order $1$
		- $\mathcal{Z}/2\mathcal{Z} \times \mathcal{Z}/2\mathcal{Z}$:![[Pasted image 20231222013645.png]]
			- Order $2$
				- Order $1$
			- Order $2$
				- Order $1$
			- Order $2$
				- Order $1$
***
- **Commutative groups $G$, with $x^p = 1 \,\forall\, x \in G, \text{ where p is prime}$**:
	- Write Group Operation as *addition* instead of *multiplication*.
	- Then $G$ is a vector space over $\mathcal{F}_p$ ($p$ elements) = Finite [[Field]], it can be viewed as scalar **Field** for vector space.
		- $p.x = 0$, it is $x^p = 1$ written additively, as $x^p = \underbrace{x + x + \ldots + x}_{p \text{ times}} = p \cdot x$, in additive group, and *identity* is represented by $0$ instead of $1$.
	- Any vector space over a **Field** is a sum of $1-D$ vectors **isomorphic** to the field.
	- So, $G$ is **isomorphic** to $\mathcal{F}_p^n$ (*considering $n$ - dim vector space, finite*).
	- So, $G$ has order $p^n$ for some $n$, and $G \cong \mathcal{F}_p^n$.
	- $G$'s are called **Elementary Abelian $p-$Groups**. And, next to **cyclic** groups these are some of the simplest possible groups.
***
- $0 \to A \to B \to C \to 0$
	- Here these arrows are **Homomorphisms**.
	- This sequence is *exact at $B$* if **image of $A \to B$** is **kernel of $B \to C$**.
	- $0 \to A$ is an *Injection*. $C \to 0$ is an *surjection*.
	- If we look at $0 \to A \to B$, then
		- It is *exact* if **image of $0 \to A$** is **kernel of $A \to B$**; ie; it is just the *trivial subgroup of $A$ - **identity***.
	- If we look at $B \to C \to 0$, then
		- It is exact if **image of $B \to C$** is **kernel of $C \to 0$**; but here whole of $C$ goes to $0$.
	- So, this means $A$ is subgroup of $B$, and $B$ is subgroup of $C$.
	- $A \to B$, has **kernel** $0$ and **image** $A$.
	- $B \to C$, has **kernel** $A$ and **image** $C$.
	- We can write it multiplicatively as well, using $1$ instead of $0$.
- One trivial case is $0 \to A \to A \times B \to B \to 0$. (**SPLIT EXACT SEQUENCE**)
***
We can write $0 \to \mathcal{Z}/2\mathcal{Z} \to \mathcal{Z}/4\mathcal{Z} \to \mathcal{Z}/2\mathcal{Z} \to 0$. (**NON-SPLIT EXACT SEQUENCE**)
We can write $0 \to \mathcal{Z}/2\mathcal{Z} \to \mathcal{Z}/2\mathcal{Z} \times \mathcal{Z}/2\mathcal{Z} \to \mathcal{Z}/2\mathcal{Z} \to 0$.
So, we have same $A$ and $C$ but $B$ different, so, it is not possible to know from $A$ and $C$ what $B$ is.
*One absent minded mistake is to assume **exact sequence** are **split** but they can be **non-split***.
***
# Product of Groups

$G \times H = \{(g,h) \, \forall \, g \in G, h \in H\}$
$(g_1, h_1)(g_2, h_2) = (g_1g2, h_1h_2), \, for \, \{g_1, g_2\} \in G \,and\, \{h_1, h_2\} \in H$.
*By routine checking it will be a group*.

- Let, $G$ has subgroups $A$ and $B$, and they commute and every element of $G$ is of form $ab$ for $a \in A, b \in B$ in a unique way, then $G$ is **isomorphic** to $A \times B$.
	- Because, we have a **Homomorphism** from $A\times B \to G$, which take $(a, b) \to ab$ for $a \in A, b\in B$.
		- Take $(a_1, b_1)(a_2, b_2) = (a_1a_2, b_1b_2), \, for \, \{a_1, a_2\} \in A, \{b_1, b_2\} \in B$ under this map, it will go to $a_1a_2b_1b_2 = (a_1b_1)(a_2b_2)$. Hence, we can interchange map and product.
		- So, it is a **homomorphism**.
	- It is a **bijection** as every element of $G$ can be written as $ab$ in a unique way.
	- So, it is an **isomorphism**.

*Eg:* $\mathcal{R}^* \cong \{-1, 1\} \times \mathcal{R}_{>0}$
Because, every non-zero element can be written as product of positive real element with $1$ or $-1$.

*Eg:* $\mathcal{C}^* \cong S^1 \times \mathcal{R}_{>0}$
$S^1$ = circle group of unit circle.
This is ***Polar Decomposition** of a Complex Number.*

*Eg:* [[Chinese Reminder Theorem]]
$\mathcal{Z}/mn\mathcal{Z} \cong \mathcal{Z}/m\mathcal{Z} \times \mathcal{Z}/n\mathcal{Z}$, $m$,$n$ are co-prime
- **Kernel** = multiples of $m$ and $n$ ie; of $mn$ as both are co-prime so, $0$ is the **Kernel**.
- These groups have same order, and it is an injection with $0$ kernel so, it must be a **bijection**. So, we have an **Isomorphism**.
So, as we can see that,
$\mathcal{Z}/4\mathcal{Z} \ncong \mathcal{Z}/2\mathcal{Z} \times \mathcal{Z}/2\mathcal{Z}$
$\mathcal{Z}/6\mathcal{Z} \cong \mathcal{Z}/2\mathcal{Z} \times \mathcal{Z}/3\mathcal{Z}$
So, we shouldn't be casual about these things. **CAUTION!!!.**

*Eg*:$(\mathcal{Z}/mn\mathcal{Z})^* \cong (\mathcal{Z}/m\mathcal{Z})^* \times (\mathcal{Z}/n\mathcal{Z})^*$, $m$,$n$ are co-prime
here, * means taking *multiplication* as group operation.
![[Pasted image 20231222022933.png]]
We, also remember the [[Euler's Theorem]], and $x^8 \cong 1 \text{ mod }15$, but we can see it is not the best possible. Every element of the product group is dividing $4$, so $x^4 \cong \text{ mod } 15$.
So, we *tighten **Euler's Theorem** using this decomposition*.

*Eg:* $\mathcal{Q}^*$ : Non-zero rational numbers under multiplication.
Every Rational Number can be written as product of powers of prime in unique ways. (**Isomorphism**).
$\mathcal{Q}^* (\cong \mathcal{Z} \oplus \mathcal{Z} \oplus \mathcal{Z} \oplus \dots) \times (\mathcal{Z}/2\mathcal{Z})$
Where, lets say we have groups $A$, $B$, $C$, ... then we can form sum of groups by $A \oplus B \oplus C \oplus \dots$, (*This is only used when these groups are **Abelian***). It contains elements of form $(a, b, c, \dots)$ where **Almost all of them are 0**. So, for finite case sum of groups is same a product of groups. But for infinite case sum have almost all entries $0$.
**Almost all** -> **All but a finite number**.
We can write any $r = \pm\, 2^{n_1}3^{n_2}5^{n_3}\dots$ where $\pm$ is **isomorphic to $(\mathcal{Z}/2\mathcal{Z})$**
and, $a^{n_i}$ is **isomorphic** to $\mathcal{Z}$ where each element is mapped to base raised to its power.
So, this $$\mathcal{Q}^* (\cong \mathcal{Z} \oplus \mathcal{Z} \oplus \mathcal{Z} \oplus \dots) \times (\mathcal{Z}/2\mathcal{Z})$$is true.

*Eg:* *Octahedron* has order $48$ symmetry group as $24$ rotations and $24$ reflection. So, this group splits as product of $2$ groups.
$48 \text{ symmetries } \cong 24 \text{ rotations } \times (1, -1)$, where $-1$ is an **Automorphism** takes points to their opposite points.
These $2$ individuals are **commutative subgroups**.
**Same thing happens for** *Icosahedron, Cube, Dodecahedron*.
For *Tetrahedron* **it fails**, as it has $24$ rotations and $48$ total symmetries but those don't split into $2$ groups as it doesn't have an **Automorphism** of $-1$ which take points to opposite point (*look at picture it will become clear*).

*Eg*: Group of all roots of $1$ in $\mathcal{C}$.
![[Pasted image 20231222190659.png]]Points lie on this unit circle. (It forms a dense circle). It splits as product of various *subgroups* = $\mathcal{R}_2 \oplus \mathcal{R}_3 \oplus \mathcal{R}_5 \oplus \mathcal{R}_7 \oplus \dots$, where $\mathcal{R}_p$ for each prime $p$ we take all the roots of order $p^n$ of something. These subgroups *commute from each other*. This follows from the **Chinese Reminder Theorem**.
If we take roots dividing $n$ then it is **isomorphic** to $\mathcal{Z}/n\mathcal{Z}$, it splits as $\mathcal{Z}/2^a\mathcal{Z} \times \mathcal{Z}/3^b\mathcal{Z} \times \mathcal{Z}/5^c\mathcal{Z} \times$ \times.

***
![[Pasted image 20231222185430.png]]
***





