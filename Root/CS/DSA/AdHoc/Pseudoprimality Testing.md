This **almost works** for all the practical applications.
Lets, take the set $\mathcal{Z}_n^+ = \{1, 2, \dots, n-1\}$.

We say $n$ is a ***base-a pseudoprime*** if $n$ is composite and $$a^{n-1} \equiv 1 \, (mod \, n), \tag{eq 1}$$
[[Fermat's Theorem]] implies that if $n$ is prime then it satisfies above condition $\forall \, a \in \mathcal{Z}_n^+$.
Thus, if $\exists \,  a \in \mathcal{Z}_n^+$ such that above condition is not held then $n$ is not prime.
So, $n$ is prime $\implies \text{eq 1}$.
But *converse*, is almost always true.

If $\text{eq 1}$ fails for $a = 2$ then $n$ is **composite**.
else it is **prime** or a ***base-2 pseudoprime***, but we guess it as a **prime**.
Though the errors are pretty rare.
$$\lim_{\beta \to \infty} Pr (error) \to 0$$
**But this error goes high if numbers being tested are not randomly chosen.**
Errors can never be fully eliminated due to existence of [[Carmichael Numbers]].




