*Concepts discussed here are heavily referenced and introduced in 
[[Langrange's Theorem]], where discuss about acting transitively, and orbit, fixing an element by action, etc etc.*
- **Order 6** =
	- $S_3$
		- $6$ Subgroups:
			- $S_3$ = $\{1, (1\, 2), (2\, 3), (3\, 1), (1\, 2\, 3), (1\, 3\, 2)\}$
			- $\{1, (1\, 2\, 3), (1\, 3\, 2)\}$
			- $\{1, (1\, 2)\}$
			- $\{1, (2\, 3)\}$
			- $\{1, (3\, 1)\}$
			- $1$
	- $\mathcal{Z}/6\mathcal{Z} \cong \mathcal{Z}/2\mathcal{Z} \times \mathcal{Z}/3\mathcal{Z}$
		- $4$ Subgroups:
			- $\mathcal{Z}/6\mathcal{Z}$
			- $\mathcal{Z}/2\mathcal{Z}$
			- $\mathcal{Z}/3\mathcal{Z}$
			- $0$
***
Suppose $H \subseteq G$, and $H$ is a subgroup, then can we form $G/H$. *Here we force all the elements of $H$ to be trivial*. *Eg*. $\mathcal{Z}/n\mathcal{Z}$, where all multiples of $n$ are made trivial.
Basically we want an **exact sequence** $1 \to H \to G \to G/H \to 1$, ie; we need a **Homomorphism** from $G$ to $G/H$([[Quotient Subgroup]]) and **Kernel** for that should be $H$.
$G/H$ = set of left cosets of $H$. *As we saw that any set on which is $G$ acts transitively is a set of cosets of something*.

Can we say it is a group?
Let's take $g_1H \cdot g_2H = g_1g_2H, \{g_1, g_2\} \in G$.
Problem here is $g_1H$ can be same as $g_3H$, for some $g_3 \in G$. So, what happens to this equation? Is it well defined?
In this case we have $g_3 = g_1h$, and then if I check at the equation then I should get $g_3g_2H = g_1g_2H$ ? but is it true? or I am asking is $g_1hg_2H = g_1g_2H$? is it true?
$$
\begin{align*}
g_3 = g_1h, \,\,\,\,\,\,\,\, &g_3g_2H &&= g_1g_2H \,?\\
OR,\,\,\,\,\,\,\,\,\,\,\,\, &g_1hg_2H &&= g_1g_2H \, ?\\
LHS, \,\,\,\,\,\,\,\,\,\,   &g_1g_2(g_2^{-1}hg_2)H &&= g_1g_2H, ?&&...Since,\, g_2g_2^{-1}=e\\
\end{align*}
$$That will hold provided term in bracket $g_2^{-1}hg_2\in H$. Is it the case?
Following conditions are equivalent:
- $H$ is **kernel** for map from $G \to \text{some }X$.
- $gHg^{-1} = H, \forall g \in G$.
- $gH = Hg, \forall g \in G$.
- Left cosets are same as Right cosets.
- Quotient Group $G/H$ exists.
These are equivalent and if a $H$ satisfies any of these then we call it [[Normal Subgroup]].
***
- If $G$ is **Abelian** then we call all subgroups are **Normal**.
- All subgroups of index $2$ are **Normal**.
	- Only cosets are things in $H$ and $H'$.
		- As, $G$ must contain identity, so we get coset of identity as $H$, and we have $2$ cosets so, other one is $H'$.
	- That is exactly the same as right coset.
	- So, it is **normal**.
***
*Eg:* Which subgroups of $S_3$ are normal?
$1$, and $S_3$ are **Normal**.
$\{1, (1\, 2\, 3), (1\, 3\, 2)\}$, and all subgroups of index $2$ are normal.
$\{1, (1\, 2)\}$, and other ones of Order $2$, and index $3$, is not normal.
	- Left Cosets
		- $\{1, (1\, 2)\}$
		- $(1\, 2\, 3) \times\{1, (1\, 2)\}$ = $\{(1\, 2\, 3), (1\, 3)\}$
		- $\{(1\, 3\, 2), (2\, 3)\}$
	- Right Cosets
		- $\{1, (1\, 2)\}$
		- $\{1, (1\, 2)\times (1\, 2\, 3)\}$ = $\{(1\, 2\, 3), (2\, 3)\}$
		- $\{(1\, 3\, 2), (1\, 3)\}$
	- So, Left and Right Cosets are not same.
***
- If $H$ is a subgroup then $gHg^{-1}$ is a subgroup, and this is called **conjugate of $H$ by $g$**. This is action of $g$ on subgroup $H$.
	- Action $g(H) = gHg^{-1}$.
	- If $H$ is **Normal** then this action maps group to itself.
		- $G$ fixes this under **Conjugate action**.
	- **Conjugation** is actually a symmetry of the group, as $gabg^{-1} = gag^{-1}\,gbg^{-1}$.
	- So, if $H$ is not **Normal** then its **Conjugate** is not **Normal**.
***
*Eg*. Lets workout this for subgroups of $S_3$.
$S_3$, $<1\,2>$, $<1\,3>$, $<2\,3>$, $\{1, (1\, 2\, 3), (1\, 3\, 2)\}$
 - $<1\,3>^{-1}<1\,2><1\,3> = <2\,3>$
 - Likewise others,
 - So, all these $3$ elements form an **Orbit** under the **Conjugate action of $g$**. So, these $3$ subgroups are **conjugate**.
 - $G$ acts transitively on these $3$ subgroups.
***
When we say $1 \to H \to G \to G/H \to 1$, usually we hope $H$ and $G/H$ are smaller than $G$ and we can reduce properties of $G$ to these $2$ smaller groups. Though if we know $H$ and $G/H$ then we don't know $G$, as discussed in [[Products]] lecture.
***
**Prove**.Following conditions are equivalent:
1. $H$ is **kernel** for map from $G \to \text{some }X$.
2. $gHg^{-1} = H, \forall g \in G$.
3. $gH = Hg, \forall g \in G$.
4. Left cosets are same as Right cosets.
5. Quotient Group $G/H$ exists.
**Proof**:
$1 \implies 2$
Let, $\phi: G \to X$, then is $H \subseteq G$ (subgroup) is **Kernel** it means $\phi(H) = e_X$.
Since, $\phi$ is an **Homomorphism**, we have $\phi(ab) = \phi(a)\phi(b), \{a, b\} \in G$.
So, Let's take $g \in G$, and its **Left Coset**, and apply $\phi$ on that, $\phi(gHg^{-1}) = \phi(g)\phi(H)\phi(g^{-1}) = \phi(g)e_X\phi(g^{-1}) = \phi(gg^{-1}) = \phi(e_G) = e_X$, So, $gHg^{-1} = H$.

$2 \implies 3$
$gHg^{-1} = H \implies gHg^{-1}g = Hg \implies gH = Hg, \forall g \in G$.

$3 \implies 4$
Trivial

$4 \implies 5$
If we have $gH = Hg$ then we partition $G$ implying existence of $G/H$.

$5 \implies 1$
can define a **homomorphism** from $G$ to $G/H$,  such that $f(x) = xH$, and trivially, $H$ is $ker(f)$.

Hence, all above conditions are equivalent.
***
Size of $G/H$ is index of $H$ in $G$ or, $\frac{|G|}{|H|}$.
***


