NOT EVERY FUNCTION HAVE IT!!!!
The function need not to be periodic anymore as is the case with [[Fourier Series]]. But the formula will get more complicated.
$$x(t) = \int_{-\infty}^{\infty} X(j\omega) \cdot e^{j\omega t} d\omega$$
*Now instead of summing over integral multiples of a fundamental frequency we will be integrating over a continuum of frequencies.*
$x(t)$ will be **Inverse Continuous Time Fourier Transform**.
Where, $$X(j\omega) = \int_{-\infty}^{\infty} x(t) \cdot e^{-j \omega t} \,dt \tag{Continuous Time Fourier Transform}$$
![[Pasted image 20231218192546.png]]
***
# Decaying Exponential

*Eg:* Let, $x(t) = e^{-at}u(t), a>0$.
**Ans:** 
$$
\begin{align*}
& X(j\omega) &&= \int_{-\infty}^{\infty} e^{-at}u(t)e^{-j\omega t} dt,\\
& &&= \int_{0}^{\infty} e^{-(a + j \omega)t} dt, \\
& &&= \frac{1}{a+j\omega}, &&(...a>0, \,\text{ensures num goes to 0 at}\, t\to\infty)
\end{align*}
$$
![[Pasted image 20231215181448.png]]
The complex sinusoid can't do anything as $a$ part decays the exponential.

$$
\begin{align*}
&||X(j\omega)||^2 &&= \frac{1}{\omega^2 + a^2},\\
&|X(j\omega)| &&= \sqrt{\frac{1}{\omega^2 + a^2}}, &&(...\text{Something like Lorentz Function, not Gaussian})
\end{align*}
$$
![[Pasted image 20231215182022.png]]
***
# Impulse Function

***
