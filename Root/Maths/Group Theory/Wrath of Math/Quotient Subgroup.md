We need **Normal Subgroup** to be able to construct a **Quotient Group**.
So, Let $H$ be a **Normal Subgroup** of $G$. Then we have $G/H = \{Ha, Hb, Hc, \dots\}$, ie; set of all **cosets** of $H$ in $G$.
$G/H$ with operation *Coset Multiplication* is a group.
**Proof**:
- **Closure**: $Ha \cdot Hb = H(ab)$
- **Associativity**: 
  $$
  \begin{align*}
  &Ha \cdot (Hb \cdot Hc) && = Ha \cdot H(bc),\\
  & &&= H(a(bc)),\\
  & &&= H((ab)c),\\
  & &&= H(ab) \cdot H(c),\\
  & &&=(Ha \cdot Hb) \cdot Hc
  \end{align*}
  $$
  - **Identity**: $Ha .He = H(ae) = Ha$, So, $He = H$ is Identity element.
  - **Inverse**: $(Ha)^{-1} = a^{-1}H^{-1} = a^{-1}H = Ha^{-1}$
So, it is a Group, and called as **Quotient or Factor group of $G$ by $H$**.
By, this we can factor out some undesirable properties from $G$.
**Quotient Group** can partition $G$, as it is set of **cosets** and **cosets** partition the group.
***
**Theorem**: $G/H$ is a **Homomorphic** image of $G$.
**Proof**: 
Let $f: G \to G/H$,
$f(x) = Hx$
Any element in image will be part of **right coset** of $H$. So, it is a **surjection**.
$f(xy) = Hxy = Hx \cdot Hy = f(x)f(y)$, since $H$ is a **Normal Subgroup** so, **coset multiplication** is well-defined. So, it is a **Homomorphism**.
Hence, Proved.
***
**Theorem**: If $f: G \to H$ is a **Homomorphism** with **kernel** $K$, then $f(a) = f(b) \iff Ka = Kb$
**Proof**: 
Let, 
$$
\begin{align*}
&f(a)  &&= f(b)\\ 
\implies &f(a)(f(b))^{-1} &&= e, \\
\implies &f(a)f(b^{-1}) &&= e, &&...\text{(Since, f is Homomorphism)} \\
\implies &f(ab^{-1}) &&= e,\\
\implies &ab^{-1} &&\in K, \\
\implies &a &&\in Kb, \\
\text{Similarly, } &b &&\in Ka, \\
\therefore\, &Ka = Kb
\end{align*}
$$
Now, 
$$
\begin{align*}
& ka &&= Kb, \\
\implies &\phi(Ka) &&= \phi(Kb), \\
\implies &\phi(K)\phi(a) &&= \phi(K)\phi(b), \\
\implies &\phi(a) &&= \phi(b).
\end{align*}
$$
Hence, Proved.
***
**First Isomorphism Theorem**: If $G$ and $H$ are $2$ groups and $\phi: G \to H$ be a group **homomorphism**. Then the $ker(\phi) \stackrel{\Delta}{\_} G$, and $$G / ker(\phi) \cong Im(\phi)$$
**Proof**: The fact about $ker(\phi) \stackrel{\Delta}{\_} G$ is proved in [[Normal Subgroup]].
Look, at [[First Isomorphism Theorem]].
***


