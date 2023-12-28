*These properties will quickly run into **Region of Convergence** issue as soon as we start dealing with **Bilateral Laplace Transforms***.
# Time-Delay Property
$$
\begin{align*}
&\mathcal{L}(x(t)) &&\rightleftharpoons &&X(s)\\
&\mathcal{L}(x(t-t_0)) &&\rightleftharpoons &&e^{-s t_0}\cdot X(s)
\end{align*}
$$
Here, I am assuming $x(t) = 0, t \lt 0$, as when you write expression and do integration you would see that, lower limit of integration is changed to $-t_0$, and we need support of $x(t)$ to lie in positive region for everything to be smooth.
**CAUTION!!!** *We can shift something to the left given we have enough space so, no chopping happens at $0$. As we take integral from $0^-$.*
![[Pasted image 20231228193434.png]]
In this photo in *red color graph*, chopping happened which is wrong.
***
# Convolution Property
$$
\begin{align*}
&\mathcal{L}(x(t)*h(t)) &&\rightleftharpoons &&X(s)H(s)\\
\end{align*}
$$
***
# Time Integral Property
$$
\begin{align*}
&\mathcal{L}(x(t)) &&\rightleftharpoons &&X(s)\\
&\mathcal{L}(\int_{0^-}^t x(\tau)d\tau) &&\rightleftharpoons &&\frac{X(s)}{s}
\end{align*}
$$
Proof,
$$
\begin{align*}
&\int_{0^-}^{\infty}[\int_{0^-}^t x(\tau)d\tau]e^{-st}dt &&= [\frac{e^{-st}}{-s}\cdot\int_{0^-}^t x(\tau)d\tau]_{t=0^-}^{t=\infty} - \int_{0^-}^{\infty}\frac{e^{-st}}{-s}x(t)dt, \tag{Integration By parts}\\
(Since, \,\,& dv= e^{-st}dt=>v=\frac{e^{-st}}{-s},&&u=\int_{0^-}^tx(\tau)d\tau=>du= x(t)dt)\\
& &&= \frac{1}{s}X(s)\\
&\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,(\text{ Assuming }, s \text{ is  }&&\text{sufficiently large enough that } e^{-st}\\ &\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\text{ doesn't let } &&int_{0^-}^t x(\tau)d\tau \text{ grow fast enough for } t=\infty)&&.

\end{align*}
$$

One, more thing convolution with $u(t)$ is Integration, so, we can even use that.
***
# Frequency Shift Property
$$
\begin{align*}
&\mathcal{L}(x(t)) &&\rightleftharpoons &&X(s)\\
&\mathcal{L}(x(t)\cdot e^{\alpha t_0}) &&\rightleftharpoons && X(s-\alpha)
\end{align*}
$$Where, $\alpha$ is a general complex number, so, it essentially isn't frequency until is $\Im$, but people call it that property anyway.
***
# Time Derivative Property
$$
\begin{align*}
&\mathcal{L}(x(t)) &&\rightleftharpoons &&X(s)\\
&\mathcal{L}(\frac{d}{dt}x(t)) &&\rightleftharpoons &&sX(s) - x(0^-)
\end{align*}
$$
Proof,
$$
\begin{align*}
&\int_{0^-}^{\infty}[\frac{d}{dt}x(t)]e^{-st}dt &&= [x(t)e^{-st}]_{t=0^-}^{t=\infty} - \int_{0^-}^{\infty}x(t)(-se^{-st})dt, \tag{Integration By parts}\\
(Since, \,\,& dv= dx(t)=>v=x(t),&&u=e^{-st}=>du= -se^{-st}dt)\\
& &&= -x(0^-) + sX(s)\\
&\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,(\text{ Assuming }, s \text{ is  }&&\text{sufficiently large enough that } e^{-st}\\ &\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\text{ doesn't let } &&x(t)\text{ grow fast enough for } t=\infty)&&.

\end{align*}
$$
In most cases **Bilateral** case is same as **Unilateral**, but that $x(0^-)$ won't be there if you take **Bilateral Laplace Transform**.
We didn't do something like we did in **Fourier Transform** case, because there we used **Inverse Fourier Transform**, but here we don't know **Inverse Laplace Transform** because it is a scary-scary thing, because our transform variable is complex which was not the case in **Fourier** as there one dealt with time and other with frequency.
![[Pasted image 20231228202641.png]]
***

