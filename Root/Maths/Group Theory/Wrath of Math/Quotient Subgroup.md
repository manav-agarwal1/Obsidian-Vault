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
**Theorem** $G/H$ is a **Homomorphic** image of $G$.
**Proof**: 
Let $f: G \to G/H$,
$f(x) = Hx$
Any element in image will be part of **right coset** of $H$. So, it is a **surjection**.
$f(xy) = Hxy = Hx \cdot Hy = f(x)f(y)$, since $H$ is a **Normal Subgroup** so, **coset multiplication** is well-defined. So, it is a **Homomorphism**.
Hence, Proved.
***
