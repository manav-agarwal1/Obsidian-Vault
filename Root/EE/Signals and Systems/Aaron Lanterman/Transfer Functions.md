$$
\begin{align*}
&\ddot{y} + a_1\dot{y} + a_0y &&= b_1\dot{x} + b_0x, &&y(0^-), \dot{y}(0^-),\\
&s^2Y(s) - sy(0^-) - \dot{y}(0^-) + a_1sY(s) - a_1y(0^-) + a_0Y(s)&&= b_1sX(s) - b_1x(0^-) + b_0X(s), \\
\end{align*}
$$
We assume that inputs are instant at $0$ and initial conditions are $0^-$, so, those terms in input will be $0$. This is important because if $x(t) = cos(t)u(t)$ then $x(0) = 1$ but $x(0^-) = 0$ as it doesn't exist for $0^-$.
$$
\begin{align*}
&Y(s) = \frac{sy(0^-) + \dot{y}(0^-) + a_1y(0^-)}{s^2 + a_1s + a_0} + \frac{b_1s + b_0}{s^2 + a_1s + a_0}X(s),\\
\end{align*}
$$
Now, this
$$H(s) = \frac{b_1s + b_0}{s^2 + a_1s + a_0}$$
is called, **Transfer/System Function**.
$$y(t) = y_{natural}{t} + y_{forced}(t)$$
$y_{natural}{t}$: *Zero-Input Response*
$y_{forced}(t)$: *Zero-Initial Condition Response*
*Though some books don't use these synonymously, as they differentiate them on based of [[Fundamental Modes]]*.
$$Y_{forced}(s) = H(s)X(s)$$
So,
$$y_{forced} = h(t)*x(t)$$
And, $$H(s) = \mathcal{L}{h(t)}$$Where, $h(t)$ is **Impulse Response** of the system.
**Denominators are same and the forms of Numerators too, so, we can get a very good idea from just denominators. So, during analysis we get rid of the first term that gives $y_{natural}(t)$.**
*So, we can assume initial conditions $0$*. As, they can be dealt separately, and will have same form. So, we won't see initial conditions in problems involving analysis of **Transfer Functions**.
***
So,
$$
\begin{align*}
&Y(s) = \frac{b_1s + b_0}{s^2 + a_1s + a_0}X(s),\\
\end{align*}
$$
We should be able to have $H(s)$ and get $y(t)$.
***
*In discrete case we have $y[n]$ in terms of $y[n-a]$ and $x[n]$ and then we take [[Z-Transforms]]*.
***





