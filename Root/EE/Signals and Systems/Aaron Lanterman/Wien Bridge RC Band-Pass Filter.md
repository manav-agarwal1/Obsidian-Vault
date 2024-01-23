Diagram = [[Wien Bridge RC BandPass Filter.excalidraw]]

$$
\begin{align*}
&H(s) &&= \frac{\frac{R}{RCs + 1}}{\frac{R}{RCs + 1} + R + \frac{1}{Cs}}, \\
& &&= \frac{\frac{RCs}{RCs + 1}}{\frac{RCs}{RCs + 1} + RCs + 1}, \\
& &&= \frac{RCs}{R^2C^2s^2 + 3RCs + 1}, \\
& &&= \frac{\frac{s}{RC}}{s^2 + \frac{3}{RC}s + \frac{1}{(RC)^2}} \\
\implies&H(j\omega_n) &&= \frac{1}{3} &&...\text{Phase }0 \text{ and magnitude of } \frac{1}{3}, \text{ at peak.}
\end{align*}
$$
Comparing from [[Canonical Second Order Filters]].
$\omega_n = \frac{1}{RC}$
$2\zeta\omega_n = \frac{3}{RC}$
