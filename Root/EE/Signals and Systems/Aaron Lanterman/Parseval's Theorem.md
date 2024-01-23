# Plancherel Theorem / Pareseval's Theorem
$$
\begin{align*}
&\int_{-\infty}^{\infty}f(t)g^*(t) \, dt &&= \frac{1}{2\pi}\int_{-\infty}^{\infty}F(j\omega)G^*(j\omega) \, d\omega, \\
\implies&<f,g> &&= \frac{1}{2\pi}<F(j\omega), G(j\omega)>
\end{align*}
$$
***
For periodic signals, we can integrate over any period of periodic signals
$$
\begin{align*}
&\frac{1}{T_0}\int_{T_0}f(t)g^*(t) \, dt &&= \sum_{k=-\infty}^{\infty}a_k b^*_k
\end{align*}
$$
where $a_k$ and $b_k$ are [[Fourier Series]] coefficients of $f(t)$ and $g(t)$ respectively.
***

