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
***
# Is any relation to Z-Transform

Referring to the [[Sampling in Time, Replication in Frequency]], there we developed a mathematical model to understand what is happening in Sampling, and it is not how hardware implements it but it is there to help us understand what is happening.
*Though here we are not going from $-\infty$ to $\infty$, but start from $0$, as have defined notion of **one sided Laplace Transform***.
We take **Laplace Transform** of the generated $x_s(t) = \sum_{n=0}^{\infty}x(nT_s)\delta(t-nT_s)$.
$$
\begin{align*}
&X_s(s) &&= \int_{0}^{\infty}(\sum_{n=0}^{\infty}x[n]\delta(t-nT_s)) \cdot e^{-st} \, dt, \\
& &&= \sum_{n=0}^{\infty}x[n] \cdot \int_{0}^{\infty} \delta(t-nT_s)) \cdot e^{-st} \, dt, \\
& &&= \sum_{n=0}^{\infty}x[n] \cdot \int_{0}^{\infty} \delta(t-nT_s)) \cdot e^{-snT_s} \, dt, \tag{Sifting Property}\\
& &&= \sum_{n=0}^{\infty}x[n] \cdot e^{-snTs}, \\
& &&= \sum_{n=0}^{\infty}x[n] \cdot (e^{sTs})^{-n}, \\
&X(z) &&= \sum_{n=0}^{\infty}x[n] \cdot z^{-n} &&...z = e^{sT_s}\\
\end{align*}
$$
*So, we can say **Z-transforms** are special case when take **Laplace Transform** of a sampled signal, and do some notational manipulation*. 
$$
\begin{align*}
&z &&= e^{sT_s} &&= e^{[\Re\{s\} + \Im\{s\}]T_s}, \\
\implies &ln(z) &&= sT_s, \\
\implies &s &&=\frac{ln(z)}{T_s}, &&...CAUTION \,\, here
\end{align*}
$$

**What is $X_s(s + jk\cdot\frac{2\pi}{T_s})$?**
$\omega_s = \frac{2\pi}{T_s}$, the **Sampling Frequency**.
It will be $X_s(s)$ as, $e^{-jkn2\pi} = 1$.
So, **Sampling in Time, results in replication on the S-Plane along the imaginary axis**.
***
# Mapping between s-plane and z-plane
*From derivations in previous section*.
$$
\begin{align*}
&z &&= e^{sT_s} &&= e^{[\Re\{s\} + \Im\{s\}]T_s}, \\
\implies &ln(z) &&= sT_s, \\
\implies &s &&=\frac{ln(z)}{T_s}, &&...\text{PRINCIPAL VALUE}
\end{align*}
$$
![[Pasted image 20240118062743.png]]
- **S-Plane**
	- *Imaginary Axis*: Same role as the **unit circle** in **Z-Plane**.
		- Moving up from origin on Imaginary axis here is like moving *counter clockwise* on **Z-Plane** along the **unit circle** from $0$ to $\pi$.
		- Moving down from origin on Imaginary axis here is like moving *clockwise* on **Z-Plane** along the **unit circle** from $0$ to $-\pi$.
	- *Real Axis*: If something is $\Re\{s\} \gt 0$, then it corresponds to $e^{\Re\{s\}} \gt 1$, so, that is outside the **unit circle** in **Z-Plane**, and vice versa
		- This makes sense as when we have **Poles** on $RHS$ then we **unstable systems**.
- **Z-Plane**
	- Anything landing on the **Unit circle** is **Marginally Stable**.
**QUADRANT MAPPING**:
![[Pasted image 20240118063926.png]]
**Aliasing**:
The spread in **S-Plane** is $\omega s$ in length, but at every $\omega s$ it repeats. *This is one of the primary reasons we like to use **Z-Plane** for **Discrete Time Systems** as it allows us to not think about these copies*. These multiple copies cause the copies of **Poles** and **Zeroes**.
Now if there are multiple copies then say we have **poles** on $\Im\{s\}$ so, it will map to **unit circle** in **Z-Plane** but so, will all the copies, in the $e^{sT_s}$ that will be fine but then *mathematically well defined Property* is in danger for the case of $\frac{ln(z)}{T_s}$.
So, to deal with that when we write that we use the term **Principal Value**, to explain that when we map back we will always refer to the one in **central strip**.
![[Pasted image 20240118064801.png]]
Now for the case of [[FIR Filters]], we have **poles** at origin and that is not covered under this mapping as $ln(0)$ is not defined.
***
Here Professor tried to create some imaginary transform,
![[Pasted image 20240117114651.png]]
![[Pasted image 20240117114749.png]]
Basically comparing the differentials in case of **Laplace**, **Z**, and **Custom** transform.
Its essentially equivalent as we can have a notational change as done in previous section in same note and you realize you arrive at same conclusion. So, Prof Lanterman's personal head canon is that, *While coming up with these transforms initially someone must have arrived at the form similar to what we have in **custom case** but then it was notationally inconvenient so, they some manipulation and arrived at form like **Laplace Transform***.
***




