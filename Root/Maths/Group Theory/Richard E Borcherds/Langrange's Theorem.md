From *Book1 - Table 1.12*

- **Order 1** = Trivial Group
- **Order 2** = $\mathbb{Z}/2\mathbb{Z}$ (Cyclic Group of order 2)
- **Order 3** =  $\mathbb{Z}/3\mathbb{Z}$
***
**Langrange's Theorem** : Order of subgroup $H$ of group $G$, divides order of $G$.$$|G| \,mod(\,|H|\,) = 0$$
**Corollary**: Order of an element of $G$ divided order of $G$.
**Order of an element of $G$**: Smallest $n\geq0$ such that, $g^n=1$, where $g \in G$.
So, for *eg*, order of $e = 1$.
- So, if we have $g\in G$ such that, $g^n=1$, then $H = \{1, g^2, ..., g^{n-1}\}$ forms a subgroup of $G$ with $|H|=n$.

**This can help classify certain groups of finite order**.
***
- If group has order $p$ where $p$ is prime, then groups can only have elements with order $1$ or $p$. So, if group has an element $g\in G$ of order $p$, then we can write $$G = \{1, g, g^2, ..., g^{p-1}\}$$
	- So, $G$  is cyclic.
	- There is obvious [[Homomorphisms|Isomorphism]] to $\mathbb{Z}/p\mathbb{Z}$
	- So, this is classification of all groups with *prime order*.
***
*In general, classification of group doesn't depend on the size of order, but on number of **prime factors** dividing the order.*
***
**Proof of Langrange's Theorem:**
Suppose, $G$ acts on set $S$. Pick some $s \in S$, and look at $H = \{g \in G \, | \, gs = s\}$ By trivial checking we can see that $H$ is a subgroup of $G$. *So, we can look at many $s \in S$ and make many subgroups from $G$ by picking elements that fix $s$.*
*Eg:* take icosahedron and take subgroup of symmetries that fix one vertex. Sometimes vertices will point to same subgroup, sometimes we can generate by fixing more vertices (by fixing a triangle and mapping it to itself), sometimes we can fix an edge.

Now, lets ask **converse**.
Suppose, $H$ is a subgroup of $G$ can we find a set $S$ and a $s \in S$, such that $H$ fixes $s$. Answer is **Yes**.
**Why?**
**Ans:**
Lets pick $G$ = $6$ symmetries of a triangle, $S$ be a triangle.
![[Pasted image 20231218000520.png]]If, I take *blue* point then I can map it to $3$ points, if I take *red* point then I can map it to $6$ points. If point taken in middle then it is only mapped to itself. This is actually called **Orbit** These $3$ blue points are called **Orbit of $G$ on $S$**. So, $S$ acted upon by $G$ splits up into **orbits**.
- Two points are equivalent if $g \in G$, maps one to the other, and it is an *equivalence relation*.
	- **Proof**:
		- *Reflexive:* $\exists e \in G$, such that, $es = s$, $s \in S$, as $e$ is identity.
		- *Symmetric*: If $\exists g \in G$ such that for $\{s_1, s_2\} \in S$, $gs_1 = s_2$, then $\exists g^{-1} \in G$ such that, $g^{-1}s_2 = s_1$.
		- *Transitive*: if $\exists \{g_1, g_2\} \in G$ such that for $\{s_1, s_2, s_3\} \in S$, $g_1s_1 = s_2$, $$\begin{align*}&g_2s_2 &&= s_3, \\ &g_2(g_1s_1) &&= s_3, \\ & (g_2g_1)s_1&&= s_3,\\&g_3s_1 &&= s_3. &&...g_3\in G \text{ (Closure) }\end{align*}$$
	- Hence, *Equivalence Relation*.
- So, all the **Orbits** are *Equivalence Classes*.
- Action of $G$ on $S$ is *transitive*, if that point only have one **orbit**.

Suppose $G$ acts *transitively* on $S$ and let $H$ be the fixed group of $s \in S$. How can we reconstruct $S$ from $H$ and $G$?
Pick some $s \in S$, such that $H$ fixed $s$. then all other $t \in S$ are of the form $t = gs$, for some $g \in G$. Multiple points in $G$ can map $s$ to $t$.
Let, $t = g_1s$, $g_1\in G$ and $t = g_2s$ $,g_2\in G$
Now,
$$
\begin{align*}
& g_2^{-1}t &&= s, \\
& g_2^{-1}g_1s &&= s.
\end{align*}
$$
So, $g_2^{-1}g_1 \in H$, as it fixes $s$.
So, $g_1 \in g_2H$, and this $g_2H$ is called **Left Coset of $H$**.
Similarly, we can say $g_2 \in g_1H$.
So, $g_1H = g_2H$. We can identity $s$ with **Left [[Cosets]]** of $H$.
ie; For any $t \in S$, it corresponds to $\{g \in G \, | \, gs = t\}$. And, these are **Left Cosets**.
If we have **Left Coset** $gH$, then we can get $gs$, not matter which element of the **Coset** we take.
**Left Coset**: Elements of a set acted on by $g$.
**Right Coset**: *Eg:* $Hg$.
So, this suggest how to reconstruct $S$ from $G$.
$S$ = set of **Left Cosets** of $H$. Check whether this is a nice set on which $G$ acts.
1. Any 2 **Cosets** $g_1H$, $g_2H$ are *same* or *disjoint*.
	-  Say, 2 **cosets** are not disjoint then $g_1h_1 = g_2h2$ it implies $g_1 = g_2h_3$, where $h_3 = h_2h_1^{-1}$, so, $g_1H = g_2h_3H$, ie; $g_1H = g_2H$.
	- $G$ is a *disjoint* union of $gH$ **cosets**
	- $G$ acting on $gH$ is $g_1(gH)$, for $g_1 \in G$.
		- And, it is a group action. (Check group axioms).
We have seen,
- *So, we have shown that if $G$ acts on $S$ then we can get subgroups $H$ from it, and **conversely** if we have $H$ subgroups of $G$ then we can construct set $S$ such that $H$ comes from action of $G$ on $S$*.
- *Any two **cosets** have same size*.
	- Any **coset** has size equal to $H$.![[Pasted image 20231218004555.png]]
	- Here we uses *inverses*.
	- If we remove *inverses* we get **semigroups** and there, also we define **cosets** but they don't have same size.
So, **any $G$ = disjoint union of cosets of $H$, and al cosets are of same size**. Hence, $$|G| = |H|*\text{ number of cosets }$$Therefore, $|H|$ divides $|G$|$.
Hence, Proved.

**This is really useful in determining order of a group**.
***
*Eg*: Take icosahedron![[Pasted image 20231218005059.png]]
And, take $H$ = symmetries that fix top point.
Now, there are $5$ symmetries, and number of cosets = number of vertices = $12$
Therefore, $|G| = 5*12 = 60$.

Alternatively, $H$ = subgroup fixing one triangle to itself = order $3$.
And, number of triangles = $20$
So, $|G| = 3*20 = 60$.
***
# Application of Legrange's Theorem
- [[Fermat's Theorem]]
	- $x^p \cong x \text{ mod } p$, where $p$ is prime
	- or, $x^p-x$ is divisible by prime $p$.
	- How do we get this from **Langrange's Theorem**?
		- Order of $g \in G$ divides $|G|$, as from $g \in G$ we can get a subgroup and order of subgroup divides $|G|$.
		- So, $g^{|G|} = 1$,  as $|G|$ is multiple of $|g|$, and $g^{|g|}=1$.
			- Take, $G = (\mathbb{Z}/p\mathbb{Z})^*$
			- If, something is non-zero in $\mathbb{Z}/p\mathbb{Z}$, then it has inverse ie; we can solve $$ax+bp=1$$For, $a \in \mathbb{Z}/p\mathbb{Z}$, which is co-prime to $p$. ie; $x = a^{-1} \text{ mod } p$.
			- So, we have a group of order $p-1$
			- So, if $x \neq 0 \in \mathbb{Z}/p\mathbb{Z}$, then $x^{p-1} \cong 1 \text{ mod }p$.
			- Multiply both sides by $x$, we get $x^p \cong x \text{ mod }p$.
		- And, it also holds for $x = 0$.
- [[Euler's Theorem]]
	- Extension to **Fermat's Theorem**
	- If $x$ is co-prime to $m \gt 0$, then$$x^{\phi(m)} \cong 1 \text{ mod }m$$where $\phi(m)= \text{ Euler's Function }$
	- Look at $G = (\mathbb{Z}/m\mathbb{Z})^*$ = All integers mod $m$, that are coprime to $m$.
	- So, $x^{|G|} \cong \text{ mod } m$, if $x \in G$.
	- $|G| = \phi(m)$.
	- *Eg:* $m=12$, and $\mathbb{Z}/12\mathbb{Z} = \{1, 5, 7, 11\}$
		- $\phi(12) =4$
		- ![[Pasted image 20231218011335.png]]
		- But, we have ![[Pasted image 20231218011345.png]]
		- So, **Euler's Theorem**, is a bit sloppy there.


