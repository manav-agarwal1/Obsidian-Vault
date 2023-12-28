*We will look at **Double Side Band AM***.
![[Pasted image 20231223184137.png]]
We need to do something to $x(t)$ for it to travel through the atmosphere, one thing is we can turn them into EM waves but EM waves at audio frequencies don't like to travel through the atmosphere, and moreover, to generate them we will need a huge antenna. So, we don't do that.

We modulate $x(t)$ to create $m(t)$ and we need demodulator in car.
$m(t) = x(t) cos(\omega_c t)$
`cosine` is the **carrier**.
We assume that $x(t)$ is *band limited* to some highest frequency $\omega_b$![[Pasted image 20231223190753.png]].
We can also assume x(t) is real-values so, this diagram is drawn with *conjugate symmetry*.
We know [[Fourier Transforms#Sinusoids|Fourier Transform]] of `cosine`.
$$
\begin{align*}
&M(j\omega) &&= \frac{1}{2\pi}X(j\omega)*\pi.[\delta(\omega-\omega_c)] + \delta(\omega+\omega_c)]\\
& &&= \frac{1}{2}[X(j\omega)*\delta(\omega-\omega_c) + X(j\omega)*\delta(\omega+\omega_c)]\\
& &&= \frac{1}{2}[X(j(\omega-\omega_c)) + X(j(\omega+\omega_c))] &&...\text{Seen During Convolution discussion}\\
\end{align*}
$$
![[Pasted image 20231223191808.png]]
`cosine` shifted the $x(t)$ to higher frequency so, it can travel through atmosphere.
***
Now, how to Demodulate it?
If we do something like![[Pasted image 20231223192316.png]]Then it will be painful as `cosine` crosses $0$ a lot, so, it will be division by $0$, then we need this `cosine` to be *completely phase locked* with the `cosine` at sending end, and even a very small offset can mess things up. DONT!!!!.
***
*Though what we are about to see has problem with **Phase Mismatch***.
![[Pasted image 20231223192607.png]]
Lets, $r(t) = m(t)cos(\omega_ct) = x(t)cos^2(\omega_ct)$.
We will think about this in *Frequency Domain*.
Now, the $2$ copies generated above will have $2$ copies each with two at $\{0, 2\omega_c\}$ and other at 
$\{0, -2\omega_c\}$. The ones on the edge will have $\frac{A}{4}$ but on $0$ we will have $2$ copies so, it will have $\frac{A}{2}$.
![[Pasted image 20231223193127.png]]
We, need to get rid of $2\omega_c$ and $-2\omega_c$ copies. That will leave me with just one copy.
We need a filter $h(t)$ such that $y(t) = r(t)*h(t)$. I need $y(t)$ to be equal to $x(t)$, so, I will have cutoff at $\omega_b$, and height of $H(j\omega)$ $2$ as that will cancel $2$ in $\frac{A}{2}$.
![[Pasted image 20231223193422.png]]
Though, perfect filters are not possible in real life, but we can build something reasonably close.
***
# Real case
![[Pasted image 20231223194220.png]]
Receiver tracks the envelop, if we assume both `cosines` are phase locked.

In real system we will add some DC value to $x(t)$.![[Pasted image 20231223194339.png]]
This creates these copies of $x(t)$ at $B$ and $-B$, and fill it densely upon action of `cosine`.
At receiver we rectify it ie; take modulus, and then this happens:
![[Pasted image 20231223194618.png]] -> ![[Pasted image 20231223194631.png]]
Then we run it through LPF to smooth out![[Pasted image 20231223194653.png]]
***
# Caveats
-  We need to choose $\omega_c$ such that both copies in modulation step don't overlap. So, $\omega_c$ needs to be sufficiently bigger than $\omega_b$.
- Issue can be there is there is phase mismatch between modulation and demodulation `cosine`. If that don't happen then the copies landing on demodulation at $0$ will partially cancel each other.
- If $\omega_c$ in modulation and demodulation `cosine` mismatch then the copies landing at $0$ will not overlap giving weird funky distorted sound.
***




