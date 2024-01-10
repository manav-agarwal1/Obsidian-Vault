For all odd $n$, $n-1$ is even and we can write $$n-1 = 2^s \cdot d, \, d \, \text{ is odd}$$
So, extending on [[Fermat's Little Theorem]],
$$
\begin {align*}
& a^{n-1} \equiv 1 \, mod \,n && \iff a^{2^sd} - 1 \equiv 0 \, mod \,n, \\
& && \iff (a^{2^{s-1}d} - 1)(a^{2^{s-1}d} + 1) \equiv 0 \, mod \,n.\\
\end {align*}
$$
So, on we break and after a point we cant split, and $n$ has to divide one of those atomic terms.
