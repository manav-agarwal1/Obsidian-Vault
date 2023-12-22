**CONVOLUTION IS NOT MULTIPLICATION !!!**
***Convolution** is  **Linear** and **Time-Invariant** operation.*
For any input signal $x(t)$ to a LTI system with impulse response $h(t)$, we know, $$y(t) = \int_{-\infty}^{\infty} x(\tau) \cdot h(t-\tau) d\tau = \int_{-\infty}^{\infty} h(\tau) \cdot x(t-\tau) d\tau = (x * h)(t)$$
But, we can use this slightly incorrect notation $x(t) * h(t)$.
***Convolution** is **commutative**.*

- Terms with just $\tau$ are the fixed functions, and terms with $t-\tau$ are the functions that do through flip and shift together.

*Eg:* We have a LTI system with Impulse Response: $h(t) = e^{-4 \cdot (t-3)} \cdot [u(t-3) - u(t-6)]$, and input signal: $x(t) = t \cdot [u(t-1) - u(t-2)]$. Find the output $y(t)$.
**Ans:** Randomly, we will keep $h(t)$ fixed and flip&shift $x(t)$,
Thinking about, $x(t-\tau) = x(-(\tau - t))$, as I increase 
$x(t-\tau) = (t-\tau) \cdot [u(t-\tau-1) - u[t-\tau-2]]$,
$(t - \tau - 1) \geq 0 => (t-1) \geq \tau$ and $(t - \tau - 2) \geq 0 => (t-2) \geq \tau$
Range of activity of $x(t)$ is in $[t-2, t-1]$,
If we increase $t$, graph should go to the right, and if we decrease $t$ graph should go to left.
![[Pasted image 20231209190048.png]]
Now the **point wise multiplication** between the two graphs is $0$ when there is no overlap. This happens when,
$t - 1 \lt 3 => t \lt 4$, and $t - 2 > 6 => t > 8$.
$$
y(t) = 
\begin{cases}
0, \, &&\text{if} \,t \lt 4,\\
\int_{3}^{t-1} (t-\tau) \cdot e^{-4 \cdot (\tau-3)} d\tau, \, &&\text{if} \, t \in (4, 5)\, \text{or} \, 3 \in (t-2, t-1), &\text{Partial Overlap}\\
\int_{t-2}^{t-1} (t-\tau) \cdot e^{-4 \cdot (\tau-3)} d\tau, \, &&\text{if} \, t \in, (5,7)\, \text{or}\, ((t-1) < 6 \& (t-2) > 3), &\text{Complete Overlap}\\
\int_{t-2}^{6} (t-\tau) \cdot e^{-4 \cdot (\tau-3)} d\tau, \, &&\text{if} \, t \in (7, 8)\, \text{or} \, 6 \in (t-2, t-1), &\text{Partial Overlap}\\
0, \, &&\text{if} \,t \gt 8.\\
\end{cases}
$$*Note: We have incorporate effects of [[Unit Step Function]] in the limits.*
In *Partial Overlaps*, limits are selected on the basis that interesting thing happens only between the mutual area, so, one comes from the edge of purple block and other comes from the edge of blue block, In *Complete Overlap*, the interesting things are captured by edged of blue block.

*Trick: **Support of x(t) be $[a, b],$** and **Support of h(t) be $[c,d]$**, then **Support of y(t) be $[a+c, b+d]***. In our case we get $[1, 2]$ + $[3, 6]$ = $[4, 8]$.

**Q.** *What happens at transition points?*
**Ans:** Output generally, have some sort of continuity.

***
# Math

$$\int udv = uv - \int vdu, \tag{1}$$
**Q.** $$
\begin{align*}
&\int (t-\tau)e^{-4(\tau - 3)} d\tau &&= \int te^{-4(\tau - 3)} d\tau - \int \tau e^{-4(\tau - 3)} d\tau, \\
& &&= -\frac{1}{4}te^{-4(\tau - 3)} + \frac{\tau e^{-4(\tau-3)}}{4} - \frac{e^{-4(\tau-3)}}{16} + c, \\
& &&=\frac{e^{-4(\tau - 3)}}{16}(4\tau - 4t - 1) + c.
\end{align*}
$$

Now,
$$
\begin{align*}
&\int \tau e^{-4(\tau - 3)} d\tau && = \int \tau e^{-4\tau}e^{12} d\tau, \\
& &&=-\frac{e^{12}}{16} \int t e^t dt,  &&...(t = -4 \tau) \\
& &&=-\frac{e^{12}}{16} \int t de^t, \\
& &&=-\frac{e^{12}}{16} (te^t - \int e^t dt), &&...(\text{using (1)}), \, u = t,\, v = e^t\\
& &&=-\frac{e^{12}}{16} (te^t - e^t) + c, \\
& &&=-\frac{\tau e^{-4(\tau-3)}}{4} + \frac{e^{-4(\tau-3)}}{16} + c, &&...(t = -4 \tau)
\end{align*}
$$
***

