[Video Link](https://www.youtube.com/watch?v=KTzGBJPuJwM)
- Speed of light in glass will be slower than air (lets consider it to be a vacuum). $$ \frac{{\text{Speed of light in vacuum}}}{{\text{Speed of light in glass}}} \approx 1.52$$
- This factor is called *Index of Refraction*. The reason for calling it **refraction** is that as a consequence of this slowdown light bends by some angle.![[Pasted image 20231205124029.png]]                We can specify how much things bend by using *Snell's Law*, $$ \frac{sin(\theta_1)}{v_1} = \frac{sin(\theta_2)}{v_2} $$ Rearranging a bit, $$ v_2 = v_1\frac{sin(\theta_2)}{sin(\theta_1)} $$ So, if a white light beam is coming via vacuum and entering the prism then all the components of that white light incident at same angle ie; $\theta_1$ is same for all.
- Slow down depends on the speed of light: *High frequency => more slowdown and vice versa*.
- We can right any white light as sum of different spectral sin waves for each color and each of those terms get slowed down differently based on their frequencies, hence different angle, hence the separation.

## Why exactly do we mean by **slowing down**?
**Ans:**
- Think about glass as broken layers arranged perpendicular to the light wave.
- Lets analyze effect of only one layer:
	- It *kick back the phase.*![[Pasted image 20231205125848.png]]
	- Lets, increase number of layers gradually, ![[Pasted image 20231205130003.png]]![[Pasted image 20231205130023.png]]![[Pasted image 20231205130045.png]] So, progressively, we get a wave identical, but slower.
	- So, the correct questions will be, *Why does light's interaction with a layer of glass kick back its phase?* and *How much does light slows down?*.
	- 
### Why does light's interaction with a layer of glass kick back its phase?
*Reference to key in [[Cause of Light]]*
The glass can also be assumed as a layer of charges stacked together, and when light beams enters then by same phenomenon discussed in [[Cause of Light]] we get wiggling in the charges present in all the layers.
- Lets understand the effect of wiggling on one layer:
	- Due to wiggling of charges the glass sheet also generate a wave of its own (1 reflected and 1 in same direction of the light entering).
	- Ignoring the reflected part, if we add the generated wave and light together we get something almost identical to light wave but just shifted back in phase (exactly $90\degree$. [Why?](Feynman's Lectures). And, the successive shift in phases from all the layers give the net result of slowing down. But Why?
		- Lets, dive into adding 2 sin waves with some **Amplitude, Frequency and Phase.** Take the case of *Same frequency.*
		- Consider each wave describing *y - component* of a rotating vector with
			- Amplitude: Length of vector
			- Phase: Initial angle of vector
		- Sum of the 2 waves is now sum of those rotating vector, as since both have same frequency, then the sum locks down, so resultant, 
			- Amplitude: is magnitude of vector sum
			- Phase: is phase of vector sum
		- If :
			- *In-Phase then we get **constructive** interference. Hence, larger wave.*
			- *Out-Phase then we get **destructive** interference. Hence, smaller wave*.
		- If the **second wave is very small** and **exactly $90\degree$ out of phase to the first wave** then the resultant wave is almost identical to the first wave but little shifted back in phase. Moreover, the *Phase shift depends directly on the **Amplitude** of second wave.*
- So, ***index of refraction** depends upon how much the resultant wave by charges in layer of glass kicks back the light in **phase**.* 

### How much does it slows down? Or, more really, How strong is that phase kick?
#### Though Experiment
Lets model the charged particles in a layers as bound to some equilibrium position by a spring attached to neighboring particles. So, net force on particle if is displaced by $\vec{x}(t)$, is given by $$\vec{F}(t) = -k.\vec{x}(t)$$ie; it is directly proportional to displacement and it is accurate for small enough displacements.
This is very common thing in physics called **Linear Restoring Force.**
Now, the condition on this $\vec{x}(t)$ comes from the definition of force that comes from the newton's second law and we get, $$\frac{d^2\vec{x}}{dt^2}(t) = -\frac{k}{m}\cdot\vec{x}(t),    \text{m is mass of the particle iteself}$$
And, since we pulled particle away from equilibrium by say $\vec{x}_0$ and initial velocity $\vec{0}$. The solution, $$\vec{x}(t) = \vec{x}_0.cos(\sqrt{\frac{k}{{m}}}\cdot t)$$
Where, $$Resonant Andular Frequency (\omega_r) = \sqrt{\frac{k}{m}}$$
Now, when we pass light beam through it then the model becomes, $$\vec{F}(t) = -k.\vec{x}(t) + \vec{E}_0\cdot q \cdot cos(\omega_l \cdot t),$$$$
\begin{align*}
& \text{Angular Frequency of the light (color)} &= \omega_l, \\
& \text{Strength of the wave} &= \vec{E}_0, \\
& \text{Charge of the Particle} &= q_0
\end{align*}
$$
Now, the $\omega_l$ has nothing to with $\omega_r$, so, the resultant wave will have a transient kick off period then eventually, in steady state the frequency will become $\omega_l$. So, now the amplitude $\vec{x}_0$ which was not interesting in the previous case is the crux here, 
![[Pasted image 20231205201044.png]]
$$\vec{x}(t) = \frac{q \cdot \vec{E}_0}{m \cdot (\omega_r^2 - \omega_l^2)} \cdot cos(\omega_l \cdot t)$$
This formula is for **Steady State**.
**Denominator is interesting.**
If $\omega_l \approx \omega_r$, then the amplitude will rise and rise and rise...
Is $\omega_l$ is very small the $\omega_r$, then it takes some setup time then it finally finds a sinusoidal motion.

## Why different amount for different color?
So, the size of wiggle depends of frequency of light which determines color as well. So, more the wiggle, more the phase shift, so, *the colors whose frequencies is close to resonant frequency experience more kick back from the medium.*

So, that's why springs help model particle medium which is a **harmonic oscillator** here which makes the prism to work.

**Caveat:**
Above model misses a $-\mu \cdot \vec(v)(t)$, term which explains that certain part of lights energy is absorbed by the medium and it slowed down. 