*Eg*:
$$
\begin{align*}
&\dot{y} + 10y &&= 4sin(2t)u(t), &&y(0^-) = 1,\\
Laplace \, Tramsform,\,&sY(s) - 1 + 10Y(s) &&= \frac{8}{s^2 + 4},\\
&Y(s) &&= \frac{s^2 + 4 + 8}{(s^2+4)(s+10)}, \\
& &&=\frac{?}{s+2j} + \frac{?}{s-2j} + \frac{?}{s+10}, \\
& &&= \frac{-1-5j}{26(s+2j)} + \frac{-1+5j}{26(s+2j)} + \frac{112}{104(s+10)}, \\\\
& y(t) &&=0.1961e^{-j1.768}e^{2jt}u(t) + 0.1961e^{j1.768}e^{-2jt}u(t) + 1.077e^{10t}u(t), t\geq0\\
&  &&=  0.3922cos(2t-1.768)u(t) + 1.077e^{-10t}u(t), t\geq0
\end{align*}
$$
$y(0) = 1 = y(0^-)$, **Left Side Continuity**.
**Steady State Term**: $0.3922cos(2t-1.768)u(t)$
**Transient Term** $1.077e^{-10t}u(t)$
***


