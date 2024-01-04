*Eg*: $S_3$ of Order $6$.
Let, $A = \{1, (1\, 2)\}$, $B = \{1, (1\, 2\, 3), (1\, 3\, 2)\}$.
Then we can write $S_3 = AB$, where every element in $S_3$ is of the form $ab, a\in A, b \in B$, this is unique. So, this is an **isomorphism** from $A \times B \to S_3$ (*This is **isomorphism** of sets, Though not **isomorphism** of groups*).
The problem is $A, B$ doesn't commute.
$$
\begin{align*}
&a_1b_1 \cdot a_2b_2 &&= a_1a_2(a_2^{-1}b_1a_2)b_2,\\
\end{align*}
$$
Since $B$ is **Normal subgroup**, it is fixed under **conjugate action** of $S_3$ and any $a_i$ is member of $S_3$ so, $(a_2^{-1}b_1a_2) \in B$.
In general we can write $x^{-1}yx = y^x$, the reason for this notation is that it satisfies the rule for the exponents.
$(y_1y_2)^x = y_1^x y_2^x$, $y^{x_1x_2} = (y^x_1)^{x_2}$.

- So, we have a subgroup $A$ and a **Normal** subgroup $B$ then we have $G = AB$ uniquely.
	- We also have a right action of $A$ on $B$, for any $b \in B, a \in A$, we have $b^a$, 
		- this preserves products if $B$. ie; $(b_1b_2)^a = b_1^ab_2^a$.
		- $b^{a_1a_2} = (b^a_1)^{a_2}$
	- We can say it is a **Homomorphism** from $A$ to symmetries of $B$.

Now,
Conversely, given $A$ and $B$ can we construct a group $G$, with properties above:
- Given $A$ and $B$ and Right action of $A$ on $B$.
- Construct a group $G$ such that $A$ is a subgroup and $B$ is a **Normal** subgroup of that group, where this right action is given by **conjugation**.
We take $G = set \, A \times B$,
and define $(a_1b_1)(a_2b_2) = (a_1a_2)(b_1^{a_2}b_2)$ is $G$ a group?
- Only tricky one here to check here is *Associativity*.
	- Let  $\{a_1b_1, a_2b_2, a_3b_3\} \in G$, 
	- then $(a_1b_1\cdot a_2b_2) \cdot a_3b_3 = (a_1a_2b_1^{a_2}b_2)\cdot a_3b_3 = a_1a_2a_3(b_1^{a_2}b_2)^{a_3}b_3 = a_1a_2a_3b_1^{a_2a_3}b_2^{a_3}b_3$
	- also,  $a_1b_1\cdot (a_2b_2 \cdot a_3b_3) = a_1b_1 \cdot (a_2a_3b_2^{a_3}b_3) = a_1a_2a_3b_1^{a_2a_3}b_2^{a_3}b_3$
- *Inverse*: $(a_1b_1)^{-1} = b_1^{-1}a_1^{-1}$ which is trivially $\in G$.
- $(a_1b_1)(a_2b_2) = (a_1a_2)(b_1^{a_2}b_2)$ by this definition *closure* is there.
- Hence, $G$ is a group.
- This is called **semidirect product** of $A$ and $B$.
***
# Summary
So, given $A$ and $B$ and right action of $A$ on $B$, then we get **semidirect product** $A \ltimes B$ (*open side should be towards $B$ which is going to be **normal***), where $B$ is **Normal** subgroup, $A$ is subgroup and action taking $b \to a^{-1}ba \in A\ltimes B$, is same as give action of $A$ on $B$.
If we get left action of $A$ and $B$, then we can also form $B \rtimes A$, where also the $B$ is **Normal**, and $A$ is subgroup, just the actions have reversed.
***
*Eg* $S_3 \cong \mathcal{Z}/2\mathcal{Z} \ltimes \mathcal{Z}/3\mathcal{Z}$.
So, first one corresponds to $\{1, (1\,2)\}$, and second one to $\{1, (1\, 2\, 3), (1\, 3\, 2)\}$
***
**Goal**: We can use this to classify groups $G$ of **Order $6$**. We have to show that $G$ has to be some sort of **semidirect product**.
1. $G$ has an element $g \in G$ **Order 3**: 
	- this has to be there as by [[Langrange's Theorem]] elements in $G$ can have order $1, 2, 3, 6$.
	- If there is an element of order $6$ then it is cyclic and certainly has element of order $3$ which is $g^2$. 
	- Now suppose there is no element of order $6$ or $3$ then it will have $2$ as only non-identity order, then it implies $g^2 = 1$ so, every element is its inverse and it is abelian, then we get $\{e, h_1, h_2, h_1h_2\}$ as subgroup of $G$ but it has order $4$ and $4$ doesn't divide $6$ and so,*by contradiction*, there should be element of order $3$.
	- We get $\{1, g, g^2\}$ to be one subgroup and its *index* comes out to be $6/3 = 2$, and all subgroups of *Index $2$* are **Normal**.
2. $G$ has a subgroup of order $2$:
	-  Say, only non-identity order is $3$ then we get a subgroup $\{1, g, g^2\}$. 
	- Now, these are $3$ elements, and we have $2$ more, so, say those are $a, b$ and those will have order $3$ by assumption, and $b = a^2$ for it to make sense, so all elements of **order $3$** comes in pairs - element and its inverse. 
	- So, this would make $\{1, g, g^2, a, a^2\}$ as a subgroup, and then we have one more element $c$ somewhere not in this, and it is also of **order $3$** so its inverse is $c^2$. 
	- Now, $\{1, g, g^2, a, a^2, c\}$ but we don't have $c^{-1} = c^2$ in this G. So, *by contradiction* we need to have element with **order $2$**.
So, we have **Normal Subgroup** of **Order** $3$ and subgroup of **Order $2$**. This means $G$ is a **semidirect product** of $A$ and $B$, where $|A| = 3, |B| = 2$. Only thing we don't know is what is the action of $B$ on $A$. This will be given by **conjugation** of $B$ on $A$ in $G$. But we need to define it.
How, can $|B| = 2$, act on $|A| = 3$?
- We look at all the **Automorphisms** of $A$.
	- They should map $a \in A$ to element of same order ie; $3$ so, either to $a$ or $a^{-1}$.
	- So, group of **Automorphisms** is a group of **Order $2$**.
- There can be $2$ ways in which $B$ can act on $A$, as there can be $2$ **Homomorphisms** between groups of **order $2$**. (*Caveat: If I have $2$ groups $A$ and $B$ and i define map by **conjugate** then it will be a **Homomorphism***).
	- **Case 1**: $\mathcal{Z}/2\mathcal{Z} \times \mathcal{Z}/3\mathcal{Z}$, trivial
	- **Case 2**: Let, $\mathcal{Z}/2\mathcal{Z}$ be generate by $h$, and $\mathcal{Z}/3\mathcal{Z}$ be generated by $g$, where we are putting $g^h = g^{-1}$. This is **isomorphic** to $S_3$.
***
*Eg*: $ax + b$ group of all transformations of $\mathcal{R}$ of the form $x \to ax+b, a\neq 0$, we can represent it with matrix $(\begin{smallmatrix} a & b \\ 0 & 1 \end{smallmatrix})$. This has a **Normal** subgroup of all translations of the form $x \to x+b$, and a subgroup $x \to ax$. And, get action of subgroup which is **isomorphic** to $\mathcal{R}^*$ on the **Normal** subgroup which is **isomorphic** to $\mathcal{R}$, just as multiplication. So, if $b \in \mathcal{R}$ and $a\in \mathcal{R}$ then $b^a = ba$ (*Don't get confused by notation*).
***
*Eg:* **Isometries** (Maps from $\mathcal{R}^n$ to itself at preserved distance) of $\mathcal{R}^n$.
**Normal subgroup** = translations (which is **isomorphic** to $\mathcal{R}^n$)
Subgroup = Orthogonal Transformations (Fixing origin and given by **Orthogonal Group** which is $O_n(\mathcal{R})$ and given by Orthogonal Matrices (*Matrix that preserves distances*))
$O_n(\mathcal{R})$ acts of $\mathcal{R}^n$ and we can take **semidirect product** to get group of all [[Isometeries]].
***
*Eg*: [[Poincare Group]]
**Normal subgroup** = translations of [[Space-Time]]
Subgroup = [[Lorentz Transformations]] ([[Lorentz Group]])
![[Pasted image 20240101200723.png]]
***
**Groups of Order $7$ are cyclic, as it prime**. So next, we will classify groups of **Order $8$**.
***








