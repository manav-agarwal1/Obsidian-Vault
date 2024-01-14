[MIT Note](https://web.mit.edu/2.14/www/Handouts/PoleZero.pdf)
# Filters

*Notations*: $\omega_n = \text{Natural Frequency}$, $\zeta = \text{Damping Factor}$,
$\zeta$ is actually a ratio.
**Quality factor (Q)**: $= \frac{1}{2\cdot\zeta}$.
In below below cases **poles** will be same but just the **zeroes** will be different.
We assume for now $\omega_n \gt 0$, $\zeta \gt 0$.
If system is **BIBO stable** I can put $s = j\omega$.
$1$ is not the maximum value in case of **Low Pass Filter** and **High Pass Filter**, as it can have a transient bump before stabilizing to $1$. 
## Low Pass Filter
$$H_{LP}(s) = \frac{\omega_n^2}{s^2 + 2\zeta\omega_n s + \omega_n^2}$$
No **zeroes**.
**Sanity checks**:
- $H(j\cdot 0) = 1$
- $H(j\cdot \infty) = 0$
![[Pasted image 20240114190938.png]]
- $\omega_{resonant} = \omega_r = \omega_n \sqrt{1 - 2\zeta^2}$
	- But to make it sense $\zeta \lt \frac{1}{\sqrt2}$
***
## Band Pass Filter
$$H_{BP}(s) = \frac{2\zeta\omega_n s}{s^2 + 2\zeta\omega_n s + \omega_n^2}$$
**zeroes** = $1 \, @ \, s = 0$
**Sanity checks**:
- $H(j\cdot 0) = 0$
- $H(j\cdot \infty) = 0$
- $H(j \cdot \omega_n) = 1$
![[Pasted image 20240114190956.png]]
*Note: On the right side of $\omega_n$ graph doesn't touch to $0$, it will tail to $\infty$ as the function only has $1$ finite $0$.*
***
## High Pass Filter
$$H_{HP}(s) = \frac{s^2}{s^2 + 2\zeta\omega_n s + \omega_n^2}$$
**zeroes** = $2 \, @ \, s = 0$
**Sanity checks**:
- $H(j\cdot 0) = 0$
- $H(j\cdot \infty) = 1$
![[Pasted image 20240114191008.png]]
- $\omega_{resonant} = \omega_r = \frac{\omega_n}{\sqrt{1 - 2\zeta^2}}$
	- But to make it sense $\zeta \lt \frac{1}{\sqrt2}$
***
# Damped Oscillation and Resonant Response

We can do $H(s) = \alpha H_{LP}(s) + \beta H_{BP}(s) + \gamma H_{HP}(s)$, and we will get generic second order filter with second order polynomial in denominator, and numerator.
Keep the $\omega_n$ and $\zeta$ same. You will get same **pole** structure but we you can move **zeroes** around.

## Poles
$$
\begin{align*}
&s_p^2 + 2\zeta\omega_n s_p + \omega_n^2 &&= 0,\\
\implies &s_p &&= \omega_n(-\zeta \pm \sqrt{\zeta^2 - 1})
\end{align*}
$$
- We will get **complex conjugate poles** when $\zeta^2 - 1 \lt 0 \implies \zeta^2 \lt 1 \implies \zeta \lt 1$.
	- So, if **damping factor** is $\lt 1$ then it is **underdamped case**.
	- **poles**: $s_p = \omega_n(-\zeta \pm j\sqrt{1-\zeta^2})$.
		- Though if we keep $\zeta$ constant then we move at straight lines![[Pasted image 20240115011851.png]].
			- Cuttoff increases as we increase $\omega_n$.
		-  If $\omega_n$ is constant then it is not hard to see that $s_p$ represents point on unit circle.
			- As the poles get closer to $j\omega$ axis or complex axis that it happens when $\zeta$ is small in magnitude, and in that case if you look at [[Partial Fractions]], for complex poles case then you can see in time domain we get `sine` or `cosine`, so there are ripples in time domain, and that can cause bulge in frequency response. More ripples more prominent the bulge is.![[Pasted image 20240115003445.png]]
			- Though these ripples are only visible if the $\zeta$ is greater than $\frac{1}{\sqrt2} \approx 0.707$, ie; **poles** lie above the $45\degree$ line in unit circle visible above. Before this $\zeta$ there are no peaky behaviors like this, ![[Pasted image 20240115011223.png]]
	- **partial fraction analysis**: $$y(t) = Ae^{-j\omega_n t}e^{j\omega_n \sqrt{1-\zeta^2}}u(t) + A^*e^{-j\omega_n t}e^{j\omega_n \sqrt{1-\zeta^2}}u(t), t\geq0$$
		- This will decompose to some `cosine` with some decaying factor with it.
	- **Damped Frequency**: $\omega_d = \omega_n \sqrt{1-\zeta^2}$.
		- ![[Pasted image 20240114193911.png]]
		- If we want $\omega_d$ close to $\omega_n$ then we want small $\zeta$ but then we would have ripples as explained earlier, so we have *trade-off* here.
	- In words of Prof Lanterman: *System wants to party as hard it as it can by resonating at $\omega_n$ but it cannot due to presence of $\zeta$*.
- When $\zeta = 1$,
	- This case is called **critically damped** case.
	- Double **pole** at: $s_p = -\omega_n$.
	- $$y(t) = Ate^{-\omega_nt}u(t), t\geq0$$
- When $\zeta \gt 1$,
	- This case is called **over damped** case.
	- $$y(t) = Ae^{(-\omega_n\zeta - \omega_n\sqrt{\zeta^2-1})t}u(t) + Be^{(-\omega_n\zeta - \omega_n\sqrt{\zeta^2-1})t}u(t), t\geq0$$
![[Pasted image 20240115002528.png]]
*Taken from MIT notes marked at the top of page*.
***
*Caveat*: When $\zeta$ is very low then both **Low Pass Filter** and **High Pass Filter** exhibit behavior very close to a **Band Pass Filter**. 
- When $\zeta$ is very low then we have **poles** almost sitting on the complex axis, in that case the frequency response becomes more narrower around $\omega_n$ and rest of the spectrum is attenuated.
- This is from a **Low Pass Filter**![[Pasted image 20240115005011.png]]
- This is from a **High Pass Filter**![[Pasted image 20240115011333.png]]
- For smaller $\zeta$,
	- $$
	  \begin{align*}
	  &H_{LP}(s) &&\approx \frac{\omega_n^2}{s^2+\omega_n^2},\\
	  \implies &|H_{LP}(s)| &&\approx \frac{\omega_n}{\sqrt{s^2+\omega_n^2}}, \\
	  \implies &|H_{LP}(j\omega)| &&\approx \frac{\omega_n}{\sqrt{-\omega^2+\omega_n^2}}
	  \end{align*}
	  $$
	- $$
	  \begin{align*}
	  &H_{HP}(s) &&\approx \frac{s^2}{s^2+\omega_n^2},\\
	  \implies &|H_{HP}(s)| &&\approx \frac{s}{\sqrt{s^2+\omega_n^2}}, \\
	  \implies &|H_{HP}(j\omega)| &&\approx \frac{s}{\sqrt{-\omega^2+\omega_n^2}}
	  \end{align*}
	  $$
***
Same analysis and same peaky behaviors exist for **High Pass Filters**, ![[Pasted image 20240115011453.png]]
So, everything is same but mirrored.
***
Same is true about **Band Pass Filter**, ![[Pasted image 20240115011630.png]]
***




