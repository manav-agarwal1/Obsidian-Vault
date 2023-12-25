In discrete case we do sampling ie; sample our signal at time intervals and can write something like this: $$x[n] = x(nT_s)$$
Now, for good sampling we want, $f_s > 2f_{max}$.
***
*Now we deal with higher level of sophistication*.
- **Impulse Train** = $$p(t) = \sum_{n=-\infty}^{\infty}\delta(t-nT_s)$$![[Pasted image 20231225170701.png]]

Lets, multiply $x(t)$ by **Impulse Train**, and output is called $x_s(t)$.
Now, 
$$
\begin{align*}
&x_s(t) &&= x(t)p(t),\\
& &&= x(t)\cdot \sum_{n=-\infty}^{\infty}\delta(t-nT_s),\\
& &&= \sum_{n=-\infty}^{\infty}x(t)\delta(t-nT_s),\\
& &&= \sum_{n=-\infty}^{\infty}x(nT_s)\delta(t-nT_s), \tag{Sifting Property}.\\
\end{align*}
$$
$x[n]$ is a sequence of bunch of numbers in a computer, but $x_s(t)$ is a conceptual model, to help us think about sampling process. So, it is not $x[n]$.

Now, multiplying in time is convolution in frequency domain with extra $2\pi$.
$$
\begin{align*}
&X_s(j\omega) &&= \frac{1}{2\pi} X(j\omega)*P(j\omega)\\
& &&= \frac{1}{2\pi}X(j\omega)*\sum_{k=-\infty}^{\infty}2\pi a_k), \tag{Impulse Train is Periodic}\\
& &&=\frac{1}{2\pi}X(j\omega)*[\sum_{k=-\infty}^{\infty}\frac{2\pi}{T_s}\delta(\omega - k\frac{2\pi}{T_s})]\\
& &&= \frac{1}{T_s}\sum_{k=-\infty}^{\infty} X(j(\omega - k\frac{2\pi}{T_s}))\\\\
\text{Where, }\,\,\,\,\, &a_k &&= \frac{1}{T_s}\int_{\frac{-T_s}{2}}^{\frac{T_s}{2}} \delta(t - kT_s)\cdot e^{-j\omega_0kt} dt \\
& &&= \frac{1}{T_s}\int_{\frac{-T_s}{2}}^{\frac{T_s}{2}} \delta(t) dt, \tag{Only k=0, in this interval}\\
& &&= \frac{1}{T_s}
\end{align*}
$$![[Pasted image 20231225173119.png]]
*Both **Time** domain and **Frequency** domain looks mathematically same, it is rare, but worth noting. Another eg is **Gaussian Bell Shape***.

$X_s(j\omega)$ looks like:![[Pasted image 20231225174108.png]]
And, to get $X(j\omega)$, we need *Low Pass Filter*. *We need copies of $X(j\omega) to not overlap else we have **Aliasing***.
And,
- $\omega_{max} \lt \frac{\pi}{T_s}$![[Pasted image 20231225174304.png]]

And, from **boxcars and sinc** case we know,![[Pasted image 20231225174419.png]]
**Nyquist Shannon Reconstruction Formula**: To reconstruct any signal from its samples.
$$x(t) = \sum_{k=-\infty}^{\infty}x[n]\frac{sin(\frac{\pi}{T_s}(t-kT_s))}{\frac{\pi}{T_s}(t-kT_s)}$$
Main lobe of `sinc` function entirely focuses on the sample point, and side lobes decrease in the way that *Nearest samples have more importance than the farther ones*.

*This felt like **AM Modulation** Lecture*. **Though everything is a mathematical concept. No real system does this. This is just to grasp the working of real system**.
***
# Real System

We assumed $x_s(t)$ is made up of **Dirac Delta Functions**. But a real **ADC**, would make signal a set of rectangles![[Pasted image 20231225175842.png]], ie; *hold a sampled value for a while*. You would put it through a **LPF**, it will be just smoothing out edges![[Pasted image 20231225175950.png]].
***

