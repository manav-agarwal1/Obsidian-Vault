# Impulses
$$
\begin{align*}
& x(t)*\delta(t-a) &&= \int_{-\infty}^{\infty} x(\tau) \cdot \delta((t-\tau)-a) \,d\tau,\\
& &&= \int_{-\infty}^{\infty} x(t-a) \cdot \delta((t-\tau)-a) \,d\tau, &&...(\delta((t-a)-\tau), \, \text{Only turns on at} \, \tau =(t-a))\\
& &&= x(t-a) \cdot \int_{-\infty}^{\infty} \delta((t-a)-\tau) \,d\tau, \\
& &&= x(t-a).
\end{align*}
$$
So, we can say, ***Convolution** is a group operation with **Impulse function** being the identity element. [[Maths/Group Theory/Contents|Group]] formed by **Convolution** is abelian.*$$x(t)*\delta(t) = x(t)$$
***
# Steps
$$
\begin{align*}
& x(t)*u(t-a) &&= \int_{-\infty}^{\infty} x(\tau) \cdot u((t-\tau)-a) \,d\tau,\\
& &&= \int_{-\infty}^{t-a} x(\tau) \cdot u((t-\tau)-a) \,d\tau, &&...(u((t-a)-\tau), \, \text{Only turns on till, we flip and shift} \, \tau =(t-a))\\
& &&=  \int_{-\infty}^{t-a} x(\tau) \,d\tau.
\end{align*}
$$
So, $$x(t)*u(t) = \int_{-\infty}^{t} x(\tau) \,d\tau$$
***
# Doublets $\delta'(t)$

$$x(t) * \delta'(t) = \frac{d}{dt}x(t)$$
***
# Extending Discussion
![[Pasted image 20231210183541.png]]
$h$ represents the impulse response.

*Eg:* We have two LTI systems with impulse response $\delta'(t)$ and $u(t)$, then we can use this picture and the $h_c(t)$ would be, $\frac{d}{dt}u(t) = \delta(t)$.

*Eg:* $x(t)*u(t+5) => x(t)*[\delta(t+5)*u(t)] => [x(t)*\delta(t+5)]*u(t) = x(t+5)*u(t)$.
***
# Boxcars (Rectangular Functions)
![[Pasted image 20231210184556.png]]
![[Pasted image 20231210184722.png]]
![[Pasted image 20231210184817.png]]
*Short cut:* We know the support of result which will be sum of supports, $[0+0, 5+2] = [0, 7]$.
Then for total overlap we will have a rectangle of height 21 and base 2, so, integral will be the area and that area is 42.
before 0 and after 7 everything is 0. and Total overlap is for $t-2>0 \cap t<5$. So, draw a line then you know there would be a slope to join 0 to 42 in graph. 
***
And since, **Convolution** is a **LTI Operation**.
![[Pasted image 20231210185352.png]]
***
*Observation: We took block of length $2$ to flip and shift, and it took 2 time units to go from **noOverlap -> totalOverlap** and **totalOverlap -> noOverlap**.*
***
*So, for the equal length case we will get a **triangle**.*
![[Pasted image 20231210185921.png]]
***
# Convolving Step Functions

$$
\begin{align*}
& u(t)*u(t) &&= \int_{-\infty}^{t} u(\tau) d\tau, \\
& &&= \int_{0}^{t} u(\tau) d\tau, \\
& &&= t \cdot u(t). &&...\text{Ramp Function}
\end{align*}
$$
*Eg:* ![[Pasted image 20231210190630.png]]
***
# Exponential Decay Functions
$x(t) = e^{-at}u(t)$ and $h(t) = e^{-bt}h(t)$, we will keep $x(t)$ fixed. $WLOG$, lets say $a \gt b$.
![[Pasted image 20231210193832.png]]
For $t<0$ there is **No Overlap**.![[Pasted image 20231210193922.png]]
For $t \geq 0$, we have,
$$
\begin{align*}
& e^{-at}u(t) * e^{-bt}u(t) &&= \int_{0}^{t} e^{-a\tau}e^{-b(t-\tau)} \,d\tau, \\
& &&= e^{-bt}\int_{0}^{t} e^{-(a-b)\tau} \,d\tau, \\
& &&= -\frac{e^{-bt}}{a-b}(e^{-(a-b)\tau} - 1)
\end{align*}
$$
Therefore,
$$ y(t) = e^{-at}u(t) * e^{-bt}u(t) = \frac{e^{-bt} - e^{-at}}{a-b} \cdot u(t)$$
What about, $\lim_{{a \to b}}$ case:
$$
\begin{align*}
& \lim_{{a \to b}} \frac{e^{-bt} - e^{-at}}{a-b} &&= \frac{\lim_{{a \to b}} (\frac{d}{da} (...))}{\lim_{{a \to b}} (\frac{d}{da} (...))}, \tag{L'Hospital Rule}, \\
& &&= \lim_{{a \to b}} te^{-at}, \\
& &&=te^{-bt} = te^{-at}
\end{align*}
$$
In this case, $y(t) = te^{-at}u(t) = te^{-bt}u(t)$.
***

