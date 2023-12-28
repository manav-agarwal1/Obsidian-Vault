There are tons of things out there in space and scientist send high energy waves and then receive something in response 
Now those signals can look like this![[Pasted image 20231228163230.png]]
In order to get meaningful things we need to sample at $2f_{max} = 22 GHz$, which is not feasible from hardware perspective due to *bit depth* issue.
Now we will use some trick, there nothing out there as the *local Bandwidth* = $2 GHz$.
Let, $\omega_c = 2\pi (10 \times 10^9)$, (Center Frequency).
Let, signal be $x(t)$, now we want to multiply it by $e^{-j\omega_ct}$. and get $x_{left}(t)$.![[Pasted image 20231228163642.png]]
Reason being this multiplication shifts it to left in frequency domain, [[Fourier Transforms - Properties and Operations]].
![[Pasted image 20231228163800.png]]
Now, we just need to pass it via a **low pass filter** with cut off from -1 and 1.![[Pasted image 20231228163900.png]]
We, get $x_b(t)$, it is called **Baseband Signal**.
Now, the $x(t)$ was *real valued* so, its frequency domain was *conjugate symmetric*, but neither $x_{left}(t)$ not $x_b(t)$ is *conjugate symmetric*.
$x_b(t)$ will be *complex valued*.

So, what would it mean by multiplying complex exponential.
$e^{-j\omega_ct} = cos(j\omega_ct) - jsin(j\omega_ct)$.
So, $x(t)$, is multiplied with these $2$ copies.
Now these are still voltages and it is us who call that $\Re$ or $\Im$.
**Baseband Signal** = **Real Part**(*In - Phase Part*) + **Imaginary Part**(*Quadrature Part*). This is IQ Representation.![[Pasted image 20231228164548.png]]

*This is useful in many fields other than **Radio Astronomy***.
***











