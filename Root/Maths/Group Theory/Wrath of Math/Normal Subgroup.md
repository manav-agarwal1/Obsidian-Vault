Let $H$ be a subgroup of $G$. Then $H$ is called a **Normal Subgroup**, and we may write $H \stackrel{\Delta}{\_} G$, if $H$ is closed with respect to **conjugates**, ie; $\forall g\in G$, $gHg^{-1} \in H$.
- It is non-empty subset of $G$.
- Subgroup
	- Closed with respect to products.
	- Closed with respect to inverses.
- Normal
	- Closed with respect to conjugates
We, have equivalent condition when $gH = Hg, \forall g\in G$.
**CAUTION!!!**, if we have a left coset $aH$ and right coset $Ha$, then we are not saying that $ah = ha, a\in G, h \in H$, we are saying that $ah \in Ha$. so, it could be $ah = h'a$ where $h \neq h'$.
***
- **Abelian** subgroups are **Normal**.
***
*Q*. Let, $f: G \to X$, be a **Homomorphism**, then $Ker(f) \stackrel{\Delta}{\_} G$.
**Proof**:
Let, $\{a,b\} \in Ker(f)$, So, $f(ab) = f(a)f(b) = e\cdot e =e$, $\therefore ab \in Ker(f)$.
And, it is closed in inverses, trivial check.
So, $f(xax^{-1}) = f(x)f(a)f(x^{-1}) = f(x)f(a)f(x)^{-1} = f(x)ef(x)^{-1} = e$.
So, $xax^{-1} \in ker(f), \forall x \in G$.
***
# Coset Multiplication Operation in Normal Subgroup

Let $H$ be a subgroup of $G$.
Coset multiplication is defined as $Ha \cdot Hb = H(ab)$.
*Cosets have multiple representations. So, it is not well-defined in general.*
As, in general we can have $Ha = Hc, Hb = Hd, \text{ but } H(ab) \neq H(cd)$.

*Eg:* In $S_3$, let $H = \{1, (1\, 2)\}$
Lets, take **Right cosets**.
then, $H(2\,3) = \{(2\,3),(1\,2\,3)\} = H(1\,2\,3)$
and, $H(1\,3) = \{(1\,3),(1\,3\,2)\} = H(1\,3\,2)$
Lets, assume **coset multiplication** is well-defined.
$H(2\,3)\cdot H(1\,3) = H((2\,3)\,(1\,3)) = H(1\,2\,3)$
$H(1\,2\,3)\cdot H(1\,3\,2) = H((1\,2\,3)\,(1\,3\,2)) = H(1)$
But this is wrong, as $H \neq H(1\,2\,3)$, so, the **coset multiplication** operation is not well-defined, by contradiction.
***
**Prove** if $H \stackrel{\Delta}{\_} G$, then **coset multiplication** is a well-defined operation.
**Proof**: $Hg = gH$, as $H$ is **normal subgroup** of $G$.
$$
\begin{align*}
&Ha \cdot Hb &&= Ha \cdot bH,\\
& &&=H \cdot(ab)H,\\
& &&= H \cdot H(ab), \\
& &&= H(ab)
\end{align*}
$$
$\therefore$ it is well-defined operation in case of **normal subgroups**.
***
