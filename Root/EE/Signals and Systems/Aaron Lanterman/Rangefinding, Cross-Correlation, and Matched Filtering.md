Say, we broadcast a signal to a flying saucer to figure out how far, it is so, we will send a signal and receive the reflected version of it from the saucer.
![[Pasted image 20231212004136.png]]
*Caveat: The broadcasted signal will be flipped version of blue thing above, because real time systems need to be causal.*
Say, we broadcast $s(t)$,
What we receive is delayed s(t) and some noise, $x(t) = s(t+\Delta) + n(t)$. How to find $\Delta$(Round Trip Time)?
1. Guess $\Delta = \Delta_1$, then do $[\int_{-\infty}^{\infty} (x(t) - s(t+\Delta_1)) \, dt]^2$, ![[Pasted image 20231212004657.png]]First and third term can be ignored as they don't play any role.![[Pasted image 20231212004823.png]] OR![[Pasted image 20231212004839.png]] OR![[Pasted image 20231212004852.png]]
Though the last expression looks like convolution though not exactly.
$$
\begin{align*}
& \int_{-\infty}^{\infty} x(\tau) \cdot s(\tau - t) \, d\tau &&= \int_{-\infty}^{\infty} x(\tau) \cdot s(-(t-\tau)) \, d\tau, \\
& &&=x(t) * s(-t)
\end{align*}
$$
So, basically we just need to filter $x(t)$ with flipped version of whatever signal we broadcast to saucer. And, maximize that.
$h(t) = s(-t)$, is called **Matched Filter**, as it matches to what we sent out to the universe.
![[Pasted image 20231212012124.png]]
This makes out filter non-causal, from the **Extra** proof done below.
To make causal filter, we can just shift $h(t)$.
![[Pasted image 20231212012224.png]]
Now, **Cross Correlation** = $\int_{-\infty}^{\infty} x(\tau) \cdot s(\tau - t) \, d\tau = x(t) * s(-t) =  R_{sx}(t)$ (The part will $-t$ comes first in subscript. This is not **Convolution** of $x(t)$ and $s(t)$ but **Convolution** of $x(t)$ and $s(-t)$. 
***Cross Correlation** is not commutative.*$R_{sf}(t) = s(-t)*f(t) \neq s(t) * f(-t) = R_{fs}(t) \tag{Not Commutative}$.![[Pasted image 20231212010449.png]]
***
**Autocorrelation:**
$R_{ss}(t)$, tells how good/bad a signal is in a RADAR or SONAR kind of application.
1. $R_{ss}(t) = R_{ss}(-t)$, symmetric.
2. Peak at $t=0$.
***
**Extra:** Lets have a LTI system, with impulse response $h(t)$, then $$y(t) = \int_{-\infty}^{\infty} x(\tau) \cdot h(t-\tau) \, d\tau$$for any $x(t)$. What should be the condition for it to be causal?
**Ans:**
For $t<0$, the $t-\tau<0 => \tau > t$,
if anything comes at that point, then $y(t)$ would be using information from $x(\tau)$, with $\tau > t$, rendering the system non-causal.
**So, for ($h(t) = 0, for\,\, t<0$), for LTI system to be causal.**





