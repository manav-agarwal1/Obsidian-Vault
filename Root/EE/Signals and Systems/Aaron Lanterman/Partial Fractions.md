# Unique Roots
RHS can be thought of input to the system.
*Earlier we said **system** mapped input to output, but now we introduce concept of **state** in the system*.
**State** - Initial conditions.
**Natural Response** - *Zero-Input response*.
**Forced Response** - *Zero- Initial Condition response*.
***
*Eg* $$
\begin{align*}
&\dot{y} + 3y &&= u(t), \, y(0^-)=2 \\
\text{Laplace Transform, }\,\,&sY(s) - y(0^-) + 3Y(s) &&= \frac{1}{s}, \\
\implies &sY(s) - 2 + 3Y &&= \frac{1}{s}, \\
\implies &Y(s)[s+3] &&= \frac{1}{s} + 2, \\
\implies &Y(s) &&= \frac{2}{s+3} + \frac{1}{s(s+3)}, \\
\implies &Y(s) &&= \frac{2}{s+3} + \frac{?}{s} + \frac{?}{s+3}, \\
\implies &Y(s) &&= \frac{2}{s+3} + \frac{1}{3s} - \frac{1}{3(s+3)}, \\
\implies &y(t) &&= 2e^{-3t}u(t) + \frac{1}{3}e^{-t}u(t) - \frac{1}{3}e^{-3t}u(t), \, &&t\geq0\\
\implies &y(t) &&= [\frac{5}{3}e^{-3t} + \frac{1}{3}e^{-t}]u(t), \, &&t\geq0
\end{align*}
$$
- *So, we need **Linearity** properties mentioned in [[System Properties]], in Input, Initial Condition and between them together.*
***
*Eg* $$
\begin{align*}
&\ddot{y} + 5\dot{y} - 6y &&= 2u(t), \, y(0^-)=0, \dot{y}(0^-)= 1\\
\text{Laplace Transform, }\,\,&s^2Y(s) - sy(0^-) - \dot{y}(0^-)+ 5sY(s) - 5y(0^-) - 6Y(s) &&= \frac{2}{s}, \\
\implies &s^2Y(s) - 1 + 5sY(s) - 6Y(s) &&= \frac{2}{s}, \\
\implies &Y(s)[s^2 + 5s - 6] &&= \frac{2}{s} + 1, \\
\implies &Y(s)[(s+6)(s-1)] &&= \frac{2}{s} + 1, \\
\implies &Y(s) &&= \frac{s+2}{s(s+6)(s-1)} \\
\implies &Y(s) &&= [\frac{?}{s} + \frac{?}{s+6} + \frac{?}{s-1}],\\
\implies &Y(s) &&= [\frac{-1}{3s} + \frac{-2}{21(s+6)} + \frac{3}{7(s-1)}],\\ 
\implies &y(t) &&= \frac{-1}{3}u(t) - \frac{2}{21}e^{-6t}u(t) + \frac{3}{7}e^tu(t), t \geq 0\\
\end{align*}
$$Here we are seeing $e^t$ term which will is due to zeroes on $RHS$ of complex plane.
In [[Unit Step Function]] we said at $t = 0$ we don't know what happens to $u(t)$, but still we said we will consider it $0$, reason being this, that it allows us to leave $u(t)$ in $y(t)$, for $t\geq 0$.
$y(0) = \frac{-1}{3} - \frac{2}{21} + \frac{3}{7} = 0 = y(0^-)$, this means we have some **Left Continuity** at $t=0$.
When I check for $\dot{y}(t)$, then I have to leave out $u(t)$. *There is no good explanation of it, If you leave it there we would get $\delta(t)$ in derivative. That is not desirable.*
$\dot{y}(t) = -\frac{2}{21}(-6)e^{-6t} + \frac{3}{7}e^t$,
$\dot{y}(0) = \frac{4}{7} + \frac{3}{7} = 1 = \dot{y}(0^-)$. So, **Left continuity** here as well.

*It would get strange if input is not $u(t)$ but $\delta(t)$*.
***
# Repeated Roots
[Article Link](https://lpsa.swarthmore.edu/BackGround/PartialFraction/RootsRepeat.html)
***
# Unique and Repeated Roots
*Eg*:
$$
\begin{align*}
&Y(s) &&= \frac{1}{(s+1)(s+2)^2}, \\
& &&= \frac{?}{s+1} + \frac{?}{s+2} + \frac{?}{(s+2)^2}, \\
& &&= \frac{1}{s+1} + \frac{-1}{s+2} + \frac{-1}{(s+2)^2}. \\\\
&y(t) &&= [e^{-t} - (1+t)e^{-2t}]u(t), t \ge 0
\end{align*}
$$

