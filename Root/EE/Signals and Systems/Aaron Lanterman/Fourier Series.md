Periodic functions can be written as sum of complex exponentials (complex sinusoids with frequency $\omega_0$)
$x(t + T_0) = x(t)$, then $$x(t) = \sum_{k\,=-\infty}^{\infty} a_k \cdot e^{j\omega_0kt}$$where, $$a_k = \frac{1}{T_0}\int_{T_0} x(t) \cdot e^{-j\omega_0kt} dt$$
where, $$\omega_0 = \frac{2\pi}{T_0} \tag{Fundamental Frequency}$$
*Eg.*
![[Pasted image 20231213003013.png]]
![[Pasted image 20231213003124.png]]
![[Pasted image 20231213003155.png]]
or
![[Pasted image 20231213003223.png]]
![[Pasted image 20231213003334.png]]
![[Pasted image 20231213003432.png]]
Even when $a_k$ are complex we just make these plots with $k$ though we only have it for magnitude of $a_k$.
***
# Filtering Fourier Series

If we are given a system with impulse response $h(t)$ then we can find out output by convolving with any input signal $x(t)$, and it is obvious that is a LTI system. But sometimes this operation can be hard so, if input signal is periodic we can use ideas discussed in previous section to ease things a bit.

$$H(j\omega) = \int_{-\infty}^{\infty} h(t) \cdot e^{-j\omega t}dt \tag{Frequency Response}$$
Coincidently this looks a lot like a convolution, so
![[Pasted image 20231215173712.png]]
So, if we use the idea that we can write the input periodic signal as sum of weighted complex exponentials then we just need to multiply the coefficients of each frequency $a_k$ with appropriate frequency response.
![[Pasted image 20231215173853.png]]
*Eg:*
![[Pasted image 20231215174034.png]]
![[Pasted image 20231215174043.png]]
*Ans:* Fourier coefficients are computed as shown in previous section:
$$
a_k = 
\begin{cases}
\frac{1}{2}, \,\text{If} \, k=0,\\
\frac{sin(\frac{\pi k}{2})}{\pi k}, \,\text{If} \, k\neq0.
\end{cases}
$$
![[Pasted image 20231215174518.png]]
$H(j\omega_c)$ is the filter and based on choice of $\omega_c$ we will get the output.
Say for case $\omega_c = \frac{\omega_0}{2}$, the output is just the $y_0 = \frac{1}{2}$.
![[Pasted image 20231215174703.png]]
Say for case $\omega_c = 2\omega_0$, the output is  $y_1 = \frac{1}{2} + \frac{e^{j\omega_0t}}{\pi} + \frac{e^{-j\omega_0t}}{\pi}$. These terms are for $k=1$ and $k=-1$.
![[Pasted image 20231215175102.png]]
So, basically we are trying to have some approximation of the $x(t)$ at the output, now in the first case we got $\frac{1}{2}$ which is just straight line, then we got a sinusoid in next case which is still not a good approximation of square wave. *More and more harmonics we include by increasing the **cutoff frequency** $\omega_c$ we get to a better and better approximation of the $x(t)$.*
This is for including third harmonic in above case,![[Pasted image 20231215175537.png]]
Now, as you increase more and more harmonics you will get something like a square wave but at transition there will be sudden jumps and they will get thinner but they will be there as the **Mean Square Error** gets to 0 on average.
