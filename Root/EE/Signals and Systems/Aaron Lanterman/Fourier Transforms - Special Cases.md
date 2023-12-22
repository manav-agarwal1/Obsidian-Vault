NOT EVERY FUNCTION HAVE IT!!!!
The function need not to be periodic anymore as is the case with [[Fourier Series]]. But the formula will get more complicated.
$$x(t) = \frac{1}{2\pi}\int_{-\infty}^{\infty} X(j\omega) \cdot e^{j\omega t} d\omega, \,\, \, \, ...\text{1}$$
*Now instead of summing over integral multiples of a fundamental frequency we will be integrating over a continuum of frequencies.*
$x(t)$ will be **Inverse Continuous Time Fourier Transform**.
Where, $$X(j\omega) = \int_{-\infty}^{\infty} x(t) \cdot e^{-j \omega t} \,dt \tag{Continuous Time Fourier Transform} , \,\, \, \, ...\text{2}$$
![[Pasted image 20231218192546.png]]
***
# Decaying Exponential

*Eg:* Let, $x(t) = e^{-at}u(t), a>0$.
**Ans:** 
$$
\begin{align*}
& X(j\omega) &&= \int_{-\infty}^{\infty} e^{-at}u(t)e^{-j\omega t} dt,\\
& &&= \int_{0}^{\infty} e^{-(a + j \omega)t} dt, \\
& &&= \frac{1}{a+j\omega}, &&(...a>0, \,\text{ensures num goes to 0 at}\, t\to\infty)
\end{align*}
$$
![[Pasted image 20231215181448.png]]
The complex sinusoid can't do anything as $a$ part decays the exponential.

$$
\begin{align*}
&||X(j\omega)||^2 &&= \frac{1}{\omega^2 + a^2},\\
&|X(j\omega)| &&= \sqrt{\frac{1}{\omega^2 + a^2}}, &&(...\text{Something like Lorentz Function, not Gaussian})
\end{align*}
$$
![[Pasted image 20231215182022.png]]
***
# Impulse Function

Using eq $2$, with $x(t) = \delta(t-t_0)$:
$$
\begin{align*}
& X(j\omega)&&= \int_{-\infty}^{\infty} \delta(t-t_0) \cdot e^{-j \omega t} \,dt, \\
& &&= e^{-j\omega t_0} \tag{Sifting Property}. \\
\end{align*}
$$
Using eq $1$, with $X(j\omega) = \delta(\omega-\omega_0)$:
$$
\begin{align*}
&x(t) &&= \frac{1}{2\pi}\int_{-\infty}^{\infty} \delta(\omega-\omega_0) \cdot e^{j\omega t} d\omega, \\
& &&= \frac{1}{2\pi} e^{j\omega_0 t} \tag{Sifting Property}.
\end{align*}
$$
$$
\begin{align*}
&\mathcal{F}\{\delta(t-t_0)\} &&\rightleftharpoons &&e^{-j\omega t} \\
&\frac{1}{2\pi}e^{j\omega_0t} &&\rightleftharpoons &&\delta(\omega-\omega_0), \tag{OR}\\
&e^{j\omega_0t} &&\rightleftharpoons &&2\pi \cdot \delta(\omega-\omega_0), \tag{Since, Fourier Transforms are Linear}
\end{align*}
$$
Now, if you try to find *Fourier Transform* of $e^{j\omega_0 t}$ then you will run into trouble![[Pasted image 20231222195409.png]]
So, special cases,
$$
\begin{align*}
&\mathcal{F}\{\delta(t)\} &&\rightleftharpoons &&1 \\
&1 &&\rightleftharpoons &&2\pi \cdot \delta(\omega), \tag{Since, Fourier Transforms are Linear}
\end{align*}
$$
*Delta* and *constants* conceptually shouldn't be different.
Let's take *Inverse Fourier Transform* of $1$:
$$
\begin{align*}
\delta(t) = \, \, &x(t) &&= \frac{1}{2\pi}\int_{-\infty}^{\infty} e^{j\omega t} d\omega, \\
& &&= \frac{1}{2\pi}\int_{0}^{\infty} e^{j\omega t} d\omega + \frac{1}{2\pi}\int_{-\infty}^{0} e^{j\omega t} d\omega, \\
& &&= \frac{1}{2\pi}\int_{0}^{\infty}[e^{j\omega t} + e^{-j\omega t}] \, d\omega, \\
& &&= \frac{1}{2\pi}\int_{0}^{\infty}cos(\omega t)\, d\omega
\end{align*}
$$That means *by taking every possible `cosine` at every possible **frequency** with **amplitude** $\frac{1}{2\pi}$, I can construct a `delta` function.*
**Feel**: All, those `cosines` at $0$ are $1$, and it means those infinite number of `cosines` at every other point adds up to $0$. Well weird, but true.
***
# Sinusoids

No matter how you take it, you will run into either **by parts** or **dealing with limits**. So, clever way:
$$
\begin{align*}
&\mathcal{F}(cos(\omega_0 t)) &&= \mathcal{F}(\frac{1}{2}e^{j\omega_0 t}+ \frac{1}{2}e^{-j\omega_0t}), \\
& &&=\frac{1}{2}[\mathcal{F}(e^{j\omega_0 t}) + \mathcal{F}(e^{-j\omega_0t})], \\
& &&= \frac{1}{2}[2\pi.\delta(\omega-\omega_0) + 2\pi.\delta(\omega-\omega_0)], \tag{From above}\\
& &&=\pi.[\delta(\omega-\omega_0)] + \delta(\omega+\omega_0)]]\\\\
Similarly,\,\,\, &\mathcal{F}(sin(\omega_0 t)) &&= j\pi.[\delta(\omega+\omega_0)] - \delta(\omega-\omega_0)]]
\end{align*}
$$
***
