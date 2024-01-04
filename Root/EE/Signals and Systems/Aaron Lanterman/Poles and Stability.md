Let, transfer function be product polynomials, now it is not always true but we will talk about the common cases.
**Poles** = Roots of the denominator
**Zeroes** = Roots of the numerator
$$
\begin{align*}
&H(s) &&= \frac{b_ms^m + b_{m-1}s^{m-1} + \dots + b_1s + b_0}{a_ns^n + a_{n-1}s^{n-1} + \dots + a_1s + a_0},\\
& &&= \frac{(s-z_1)(s-z_2)\dots(s-z_m)}{(s-p_1)(s-p_2)\dots(s-p_n)},\\
\end{align*}
$$
Lets, say we can do the same for $X(s)$.
$$
\begin{align*}
&X(s) &&= \frac{(s-\widetilde{z}_1)(s-\widetilde{z}_2)\dots(s-\widetilde{z}_m)}{(s-\widetilde{p}_1)(s-\widetilde{p}_2)\dots(s-\widetilde{p}_n)},\\
\end{align*}
$$
So, we can write $$Y(s) = H(s)Y(s)$$
We can then write [[Partial Fractions]] expansion of $Y(s)$. We could have all the possibilities of unique roots, repeated roots, complex roots, mix of all this.

**Stability**: Property of the system. Generally, **poles** will come in exponent terms, and their sign will determine the stability of system.]
- If Real Part of **pole** $\lt 0$ then we have decaying terms.
- If Real part of **pole** $\gt 0$ then we have expanding terms.
- If **pole** is purely imaginary then we have forever going term, which is not expanding or decaying.
When we talk about LTI systems we only need to be concerned with **Bounded Input, Bounded Output (BIBO)** stability. For anything more we need to look at graduate level control theory.
**BIBO** means output is bounded if input is bounded. So, an LTI system can be **BIBO** stable and still give unbounded output for unbounded input.
***
It is not safe to have **poles** on the imaginary axis.

*Eg:* it can happen that system and signal both have pole on origin and then the output get $2$ poles on origin hence, the output is ramp functions which is unbounded as well. So, we got unbounded output for bounded output for this example.

*Eg* Input is sinusoid of frequency $f$ and transfer function is a sinusoid of frequency $f'$ so, in output we get sinusoids of both frequencies. If $f=f'$ then we have terms with $t\cdot cos(\dots)$ which is expanding as well. So, the $f'$ is *resonant frequency* of the system and if input had any **pole** there then we will end up having it enforce some corresponding property of system and it will expand with time. In that case this system is **Not BIBO stable**. Though it is **marginally stable**.
***
If $H(s)$ *can be written as ratio of polynomials* (**lumped system**, because if we know derivatives at certain time then we can get away with that) then system is **BIBO** stable iff it has no poles on the $RHS$ or the imaginary axis.
*Eg*: $h(t) = \delta(t) + 0.2 \delta(t-5)$ this is called a **distributed system** (If it specifies that it needs $5$ seconds worth of echo then you have to remember that). $H(s) = 1 + 0.2 e^{-5s}$, this is stable system.
*Idea of poles and zeroes is general, we don't necessarily need **lumped systems** to talk about this.*
***
**Theorem**: LTI system is **BIBO** stable if $\int_{-\infty}^{\infty} |h(t)| \, dt \lt \infty$, where $h(t)$ is **impulse response**.
***
**Marginal Stable**: No **poles** on $RHS$ but on imaginary axis.
***


