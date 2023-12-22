![[Pasted image 20231218185021.png]]
Now,
If I input real-values $Acos(\omega_0t + \phi)$, then instead of using this notation, use phasor style notation $Ae^{j\phi}e^{j\omega_0t}\}$, and provided impulse response, $h[n]$ is real-valued output can be written as $\Re\{H(j\omega)Ae^{j\phi}e^{j\omega_0t}\}$. CAUTION!!!: Here it looks like we swapped $\Re$ and $H$ as on LHS we take Real part first then on right at output we apply the system first. We can only do it because $h[n]$ is real by assumption. Input will look like this![[Pasted image 20231218185711.png]], but as a real-values convolution is an *LTI* operation then we can apply convolution with real-valued quantity without any problem. So, taking real part $\Re$, is not an *LTI* operation.![[Pasted image 20231218185845.png]]$H(j\omega) = |H(j\omega_0)|e^{j\angle H(j\omega)}$, so, output is $$\Re\{|H(j\omega_0)|Ae^{j(\phi + \angle H(j\omega)) }e^{j\omega_0t}\} = |H(j\omega_0)|Acos(\omega_0t + \phi + \angle H(j\omega_0))$$
So, the output $frequency$ is same but *Amplitude* and *Phase* are modified by the *frequency response evaluated at $\omega_0$.*
$$H(j\omega) = \int_{-\infty}^{\infty} h(t) \cdot e^{-j\omega t}dt \tag{Frequency Response}$$
Coincidently, this looks like a generic *Fourier Transform*. So, these are highly related concepts, as $H(j\omega) =\mathcal{F}\{h(t)\}$, it is *Fourier Transform of Impulse Response*.
![[Pasted image 20231218191245.png]]
***
*Eg:* $x(t) = 6cos(40\pi t + \frac{\pi}{3})$
$h(t) = e^{-50t}u(t)$. We want to find the output.
**Ans**: We, can apply the *convolution* integral but sinusoid is going in so, we should check frequency concepts first.
Given,
- $\omega = 40\pi$
- $a = 50$
So, $\mathcal{F}\{h(t)\} = \frac{1}{50 + j40\pi} = H(j\omega)$
We can normalize it to get *magnitude* and *phase*.
$|H(j40\pi)| = \frac{1}{\sqrt{50^2 + (40\pi)^2}}$
$\angle H(j40\pi) = tan^{-1}(\frac{-40\pi}{50})$
Now, result is given above.
***


