 *This lecture talks about **Digital Filter Design** using **Pole-Zero Mapping***.
 We take an **Analog Filter**, and try to arrive at **Digital** approximation of that. This is not the only procedure, there are many out there.

# Butterworth Filters

**Poles** in case of these filters are equally spaced, on the circle with radius $\omega_c$ in **s-Plane**.
**Order of Butterworth Filter $N$** = Number of poles, in the $LHS$.
![[Pasted image 20240118065827.png]]
Actually there are $2N$ **poles**, but we don't talk about *Theoretical **Poles*** on the $RHS$ as they are not **system stability friendly**.
Higher the **order**, more close to a **ideal filter**, out **Butterworth filter** will be.
*We take cuttoff at **Half power** point, at $\frac{1}{\sqrt 2} \approx 0.707$*.
$$|H(j\omega)| = \frac{1}{1 + (\frac{\omega}{\omega_c})^{2N}}$$
**Damping Ration $\zeta = \frac{1}{\sqrt2}$**
Location of **Poles** can be seen in [[Canonical Second Order Filters]].
It will work out to $s_p = -\frac{\omega_c}{\sqrt2} \pm j \frac{\omega_c}{\sqrt2}$.

*We want to create a **Discrete Time Approximation** of this Filter now*.
We map out **Laplace Plane** **poles-zeroes**to **Z-Plane** now as per the relation specified in [[Laplace Transforms]].
$z_p = e^{s_p T_s}$, $z_z = e^{s_z T_s}$ where $T_s$ is **sampling frequency**, and it should obey **Nyquist Criteria**.
Let,
$\omega_c = \frac{\omega_s}{4}$
The reason is the max frequency we can have is $\omega_s/2$ and closer $\omega_c$ is to this more weird things goes on.
After plugging the **poles** we get,
$$z_p = e^{-\frac{\pi}{2\sqrt2}}\cdot e^{\pm j\frac{\pi}{2\sqrt2}} \approx 0.3293 e^{\pm j 1.1107} = 0.3293 \angle{\pm 63.64 \degree}$$
![[Pasted image 20240118074600.png]]
$$H(z) = \frac{1}{(1 - z_{p_1}z^{-1})(1 - z_{p_2}z^{-1})}$$
In **S-Plane** we do $s-p_i$ in denominator but in **Z-Plane** *Transfer Function* we keep them together.
$$
\begin{align*}
&H(z) &&= \frac{1}{(1 - z_{p_1}z^{-1})(1 - z_{p_2}z^{-1})}, \\
& &&=\frac{1}{(1 - 0.3293 e^{j1.1107} z^{-1})((1 - 0.3293 e^{-j1.1107} z^{-1})}, \\
\implies&\frac{Y(z)}{X(z)} &&= \frac{1}{1 - 0.2924z^{-1} + 0.1084z^{-2}}, \\
\implies&Y(z) \cdot (1 - 0.2924z^{-1} + 0.1084z^{-2}) &&= X(z), \\
\implies&y[n] - 1.294 \cdot y[n-1] + 0.1084 \cdot y[n-2] &&= x[n], \\
\implies&y[n] &&= (1.294 \cdot y[n-1]) - (0.1084 \cdot y[n-2]) + x[n]
\end{align*}
$$
We have used property of [[Z-Transforms]] which are mentioned in a section of [[Laplace Transforms]].
-  $x(t) \to \text{ADC} \to H(z) \to \text{DAC} \to y(t)$.
	- Hopefully, $y(t)$ will be closed to original **Analog** $y(t)$.
	- We can approximate $H_{eff}(j\omega) \approx H(e^{j\hat{\omega}}) |_{{\hat{\omega}} = \frac{\omega}{f_s} = \frac{2\pi\omega}{\omega_s}}$.
		- Quality of approximation depends on how high sampling rate is as compared to maximum frequency, and if we have cutoff near sampling rate/2 point then we will have bad approximations.
***



















