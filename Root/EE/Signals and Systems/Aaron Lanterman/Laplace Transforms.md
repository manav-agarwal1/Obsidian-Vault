[[Fourier Transforms|Fourier Transforms]] are great and they can deal with something like decaying exponentials but will stuck with growing ones. Can we do something about it?

Lets take $x(t)$ such that $x(t) = 0, t \lt 0$.
$$X(j\omega) = \int_{-\infty}^{\infty} x(t) \cdot e^{-j \omega t} \,dt$$
This is *Fourier Transform* and we will replace the lower limit by $0^-$ to make sure $0$ is included in the integral. We do this as we have functions like $\delta(t)$ with strange singularities at the origin.
$$\mathcal{L}\{x(t)\} = \int_{0^-}^{\infty} x(t)e^{-\sigma t} \cdot e^{-j \omega t} \,dt$$
$x(t)e^{-\sigma t}$ is modified version of $x(t)$. So, I have to pick $\sigma$ such that I have something that decays fast enough to cancel expansion of $x(t)$. We assume $\sigma$ is real.
$$
\begin{align*}
&\mathcal{L}\{x(t)\} &&= \int_{0^-}^{\infty} x(t)e^{-\sigma t} \cdot e^{-j \omega t} \,dt, \\
& &&= x(t) \cdot e^{-(\sigma + j \omega)t} \,dt, \\
& &&= x(t) \cdot e^{-st} \,dt, &&...(s = \sigma+j\omega)\\
& &&=X(s).
\end{align*}
$$
*Though this is not how Laplace though it he was thinking about Probabilities and Distributions but now about signals and systems and it being extension of Fourier Transforms.* 

*Eg* Let, $x(t) = e^{-at}u(t)$
**Ans:**  Now I can handle cases with any value of $a$. It could be complex.
$$
\begin{align*}
& \mathcal{L}\{e^{-at}u(t)\} &&= \int_{0^-}^{\infty} e^{-at}u(t)e^{-s t} dt,\\
& &&= \int_{0}^{\infty} e^{-(a + s)t} dt, \\
& &&= \frac{1}{a+s}, &&...\text{For, } \Re{s} \gt -\Re{a}\\\\
\text{Look at exp term }& e^{-(\Re{s} + \Re{a})t - j(\Im{s} + \Im{a})t}&&= \text{second term is complex sinusoid, between {-1, 1}}, \\
& &&= \text{First term can explode}.
\end{align*}
$$Here, we can say $a=0$, and say $u(t)$ has $\frac{1}{s}$ as its *Laplace Transform*.
Where, $\Re{s} \gt -\Re{a}$ is called **Region of Convergence**.
What we have defined with $0^-$ is called **One Sided or Unilateral Laplace Transform**. With these we have a unique mapping from domains.
There is **Two Sided or Bilateral Laplace Transform**. But problem is that these are more difficult to deal with. Can be a couple of different cases with multiple **Region of Convergence**.
$$\mathcal{L}\{x(t)\} = \int_{-\infty}^{\infty} x(t) \cdot e^{-s t} \,dt$$
**Unilateral Laplace Transform** This has most engineering application.
***
# Sinusoids
$$
\begin{align*}
&\mathcal{L}\{cos(\omega_0t)u(t)\} &&\rightleftharpoons &&\frac{s}{s^2 + \omega_0^2},\\
&\mathcal{L}\{sin(\omega_0t)u(t)\} &&\rightleftharpoons &&\frac{\omega_0}{s^2 + \omega_0^2}
\end{align*}
$$Proof,
$$
\begin{align*}
& \mathcal{L}\{cos(\omega_0t)u(t)\} &&= \mathcal{L}\{\frac{e^{j\omega_0t}u(t)}{2}\} + \mathcal{L}\{\frac{e^{-j\omega_0t}u(t)}{2}\},\\
& &&=\frac{1}{2}[\frac{1}{s - j\omega_0} + \frac{1}{s + j\omega_0}], \\
& &&=\frac{s}{s^2 + \omega_0^2}
\end{align*}
$$
***
# Delta
$$
\begin{align*}
&\mathcal{L}\{\delta(t-t_0)\} &&=\int_{0^-}^{\infty}\delta(t-t_0) \cdot e^{-st}dt, \\
& &&=e^{-st_0}. &&..\text{For, } t_0 \gt 0.
\end{align*}
$$
For $t_0 = 0$ it is $1$.
***
# Boxcar
![[Pasted image 20231228192940.png]]
***
# Polynomials
$$
\begin{align*}
&\mathcal{L}\{\delta(t)\} &&\rightleftharpoons &&1,\\
\mathcal{L}\{u(t)\} = &\mathcal{L}\{\int_{0^-}^{t}\delta(t)dt\} &&\rightleftharpoons &&\frac{1}{s}, &&...\text{(Time Integral Property)}\\
\mathcal{L}\{t.u(t)\} = &\mathcal{L}\{\int_{0^-}^{t}u(t)dt\} &&\rightleftharpoons &&\frac{1}{s^2}, &&...t.u(t) \text{ is Ramp Function}\\
\mathcal{L}\{\frac{t^2}{2}u(t)\} = &\mathcal{L}\{\int_{0^-}^{t}tu(t)dt\} &&\rightleftharpoons &&\frac{1}{s^3}\\
& &&(\dots) \\
&\mathcal{L}\{t^nu(t)\} &&\rightleftharpoons &&\frac{n!}{s^{n+1}} &&...n \in \{\mathcal{Z}^+, 0\}\\
\end{align*}
$$
