RHS can be thought of input to the system.
*Earlier we said **system** mapped input to output, but now we introduce concept of **state** in the system*.
**State** - Initial conditions.
**Natural Response** - *Zero-Input response*.
**Forced Response** - *Zero- Initial Condition response*.
*Eg* $$
\begin{align*}
&\dot{y} + 3y &&= u(t), \, y(0^-)=2 \\
\text{Laplace Transform, }\,\,&sY(s) - y(0^-) + 3Y &&= \frac{1}{s}, \\
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

