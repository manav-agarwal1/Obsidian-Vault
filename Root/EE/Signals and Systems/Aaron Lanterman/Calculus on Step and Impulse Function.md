$$
\int_{-\infty}^{t} \delta(\tau)\,d\tau =
\begin{cases}
	0, \, \text{if} \, t \lt 0 \\
	1, \, \text{if} \, t \gt 0 \\
\end{cases}
$$For notional convenience we will write,
$$
\begin{equation}
\int_{-\infty}^{t^{+}} \delta(\tau)\,d\tau =
\begin{cases}
	0, & \text{if } t \lt 0 \\
	1, & \text{if } t \geq 0 \\
\end{cases} = u(t) \tag*{...1}
\end{equation}
$$
To get, [[Unit Step Function]]. But, we can normally get away by just writing $t$.
So, we are saying that, $$\frac{d}{dt}u(t) = \delta(t)$$But a big caveat is that $RHS$ is a [[Generalized Function]]. And, it only makes sense when we do a integral on both side in which case we arrive to *...1*. 


*Eg* $$\frac{d}{dt}cos(\pi t) \cdot u(t) = \,\,?$$
**Ans:**
![[Pasted image 20231207181643.png]]
There is a **discontinuity** at $t = 0$,
$$
\begin{align*}
& \frac{d}{dt}cos(\pi t) \cdot u(t) &&= u(t) \cdot \frac{d}{dt} cos(\pi t) + cos(\pi t) \cdot \frac{d}{dt} u(t) \tag{Product Rule} \\
& &&= -\pi \cdot sin(\pi t) \cdot u(t) + cos(\pi t) \cdot \delta(t) \tag{cos(0) = 1} \\
& &&= \delta(t) - \pi \cdot sin(\pi t) \cdot u(t)
\end{align*}
$$
![[Pasted image 20231207182801.png]]


