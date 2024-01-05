**First Isomorphism Theorem**: If $f : G \to H$, is a **Homomorphism** of $G$ onto $H$ then $$G / ker(f) \cong H$$
**Proof**: We have proved $G / H$ is **Homomorphic image** of $G$ in [[Quotient Subgroup]], and this theorem is the converse, says that **Homomorphic** image ($H$) of $G$ is **isomorphic** to **Quotient Subgroup** of $G$.
Once, we have established this we can say that ***Quotient group** and **Homomorphic images** are interchangeable ideas*.
Let, $ker(f) = K$
and $\phi: G/K \to h$ as $\phi(Kx) = f(x)$
And, it is well defined as $f(a) = f(b) \iff Ka = Kb$.

$\phi(Ka) = \phi(Kb) \implies Ka = Kb \implies f(a) = f(b)$
So, it is **injective**.

it is given then every element of $H$ is of the form $f(x)$ and clearly, $\phi(kx) = f(x)$ so it is **surjective**.

Thus, $\phi$ is **bijection**.

Now, $\phi(Ka)\phi(Kb) = f(a)f(b) = f(ab) = \phi(Kab) = \phi(Ka \cdot Kb)$ So, $\phi$ is a **Homomorphism**.

Hence, Proved.
***



