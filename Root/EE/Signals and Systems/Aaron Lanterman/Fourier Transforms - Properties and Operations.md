![[Pasted image 20231222205439.png]]***
# Time Delay Property

We know, 
$$
\begin{align*}
&\mathcal{F}(x(t)) &&\rightleftharpoons &&X(j\omega)\\
&\mathcal{F}(x(t-t_0)) &&\rightleftharpoons &&e^{-j\omega t_0}\cdot X(j\omega)
\end{align*}
$$
Now, if $x(t-t_0) = x(t)*\delta(t-t_0)$, *convolution*.
and *convolution* transforms to *multiplication* under *Fourier Transform*. So, the one more way to look at the result.
***
# Time Derivative Property
$$
\begin{align*}
&\mathcal{F}(x(t)) &&\rightleftharpoons &&X(j\omega)\\
&\mathcal{F}(\frac{d}{dt}x(t)) &&\rightleftharpoons &&j\omega \cdot X(j\omega)
\end{align*}
$$
We know that $\frac{d}{dt}x(t) = x(t)*\delta'(t)$
So, $$
\begin{align*}
&\mathcal{F}(\frac{d}{dt}x(t)) &&= \mathcal{F}(x(t)*\delta'(t))\\
& &&= \mathcal{F}(x(t))\cdot \mathcal{F}(\delta'(t))\\
& &&= \,?
\end{align*}
$$
Well, solving this thing will make me **not happy**.
So, let's do something else:
$$
\begin{align*}
&x(t) &&= \frac{1}{2\pi}\int_{-\infty}^{\infty} X(j\omega) \cdot e^{j\omega t} d\omega,\\
&\frac{d}{dt}x(t) &&= \frac{1}{2\pi}\frac{d}{dt}\int_{-\infty}^{\infty} X(j\omega) \cdot e^{j\omega t} d\omega, \\
& &&= \frac{1}{2\pi}\int_{-\infty}^{\infty}X(j\omega) \cdot\frac{d}{dt}e^{j\omega t}dt, \tag{Derivative is an LTI operation}\\
& &&= \frac{1}{2\pi}\int_{-\infty}^{\infty}X(j\omega) \cdot j\omega e^{j\omega t}dt, \\
& &&= \mathcal{F}^{-1}(X(j\omega)j\omega)
\end{align*}
$$
So, based on this calculation one side note is $\mathcal{F}(\delta'(t)) = j\omega$.
***
# Frequency Shift
$$
\begin{align*}
&\mathcal{F}(x(t)) &&\rightleftharpoons &&X(j\omega)\\
&\mathcal{F}(e^{j\omega_0t}x(t)) &&\rightleftharpoons &&X(j(\omega - \omega_0))
\end{align*}
$$
If $x(t)$ is real-values then we see *complex conjugates* in frequency domain representation.
So, the $e^{j\omega_0t}x(t)$ thing will not be real-values so, we will not necessarily have *complex conjugate symmetries*.
***
*Eg:*
$$
\begin{align*}
&\mathcal{F}(cos(\omega_0 t)x(t)) &&= \mathcal{F}((\frac{1}{2}e^{j\omega_0 t}+ \frac{1}{2}e^{-j\omega_0t})x(t)), \\
& &&=\frac{1}{2}[X(j(\omega-\omega_0)) + X(j(\omega+\omega_0))]
\end{align*}
$$
We can see the *conjugate symmetry* in frequency domain.
***


