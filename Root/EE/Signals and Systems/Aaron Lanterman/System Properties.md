# Linearity (No real system is completely linear)
*Scenario: We are in a wedding and we have DJ, they are speaking something in a microphone and playing songs say on vinyl record, and they have a mixer to add sounds of voice over the song. They also have graphic equalizers before mixer to attenuate the quality of sound. If DJ bough 2 equalizers and set them at same settings then, added to mixer, then he can save money as the equalizers are **linear** systems. They can only use 1 equalizer after mixer.*
![[Pasted image 20231207190419.png]]
Instead of this, they can do this,
![[Pasted image 20231207190458.png]]But they can only get away with this as these systems are linear.

**Linear system need to have these properties:**
1. **Superposition =** If this then both in below picture are same,![[Pasted image 20231207190745.png]]
2. **Scaling =** For this, below picture should be true.![[Pasted image 20231207190841.png]]
*Eg:* Check for linearity, $$y(t) = x(t) + 5$$**Ans:** Check for superposition, take $x_1(t)$ and $x_2(t)$,$$(x_1(t) + x_2(t)) + 5,\, \tag{if we add signal first, then pass to system}$$
$$(x_1(t) + 5) + (x_2(t) + 5) = (x_1(t) + x_2(t)) + 10, \, \tag{this is not linear}$$
*Above case is not linear, rather it is **affine**.*
With same argument,
$$
y(t) = a,
\begin{cases}
Linear, \, \text{If} \, a\neq 0,\\
Affine (Non-Linear), \, \text{If} \, a = 0,\\
\end{cases}
$$

*Eg:* Check for linearity,$$y(t) = \Re\{x(t)\}$$
**Ans:** It satisfies superposition.
Now, check for scaling:
$\alpha = \Re\{\alpha\} + j \cdot \Im\{\alpha\}$

a.  $(\Re\{\alpha\} + j \cdot \Im\{\alpha\}) * (\Re\{x(t)\} + j \cdot \Im\{x(t)\}) = \Re\{\alpha\} \cdot \Re\{x(t)\} + j \cdot (\Im\{\alpha\} \cdot \Re\{x(t)\} + \Re\{\alpha\} \cdot \Im\{x(t)\}) - \Im\{\alpha\} \cdot \Im\{x(t)\}$ So, Real part is, $\Re\{\alpha\} \cdot \Re\{x(t)\} - \Im\{\alpha\} \cdot \Im\{x(t)\}$
b. $\Re\{x(t)\} \cdot (\Re\{\alpha\} + j \cdot \Im\{\alpha\})$ = After separating reals, we get $\Re\{\alpha\} \cdot \Re\{x(t)\}$

Not, scaling, so not linear. *Though is $\alpha$ is real then it is linear.*
***

# Time-Invariance (Everything falls under this, talked under a reasonable time frame)
*This doesn't depend on system being linear, but if system is linear and time-invariant then we can bring techniques like Fourier and Laplace Transforms.*
![[Pasted image 20231208184155.png]]
So, basically **shift then system** and, **system then shift**, should produce exactly same output no matter in which direction I shift or by how much I shift.

*Eg:*
![[Pasted image 20231208185348.png]]
If, leave the $t$ alone and just do shifts, *Time-Invariance* is intact, but if do anything to $t$ like displayed above, then that will severely mess up *Time-Invariance.*

*Eg:* No $t$
Even not having $t$ is *not Time-Invariance*, eg, $y = x(3).$ This is not time invariance, as say we are looking at a function $x(t) = t$ and passing it through y, We will get out $x(3) = 3.$ Then how much how shift, it doesn't matter it will be always 3.
Now, say I shift first by 1 value $x(t-1)$, and pass to the system, I will get $x(3-1) = 2$. which is not same as 3. So, not time invariance.

*Eg:* $t$ sitting on the outside.
$$y(t) = t \cdot x(t)$$
**Not time invariant**.
System then shift => $(t+a) \cdot x(t+a)$
Shift then system => $t \cdot x(t+a)$
![[Pasted image 20231208191136.png]]![[Pasted image 20231208191540.png]]

*Eg:* $y(t)= x(t) + t$, Not Time Invariant

*Eg:* $y(t) = x(t) + 3, Not Linear but Time Invariant
***
# Causality (System that you can implement as a real time device)
A System is causal if output at a particular time doesn't depends on future inputs and current inputs.
![[Pasted image 20231208192133.png]]
*Correction: in above image it will be $\tau \geq t$*
*Eg:*![[Pasted image 20231208192506.png]]
*Eg:*![[Pasted image 20231208192750.png]]
*Eg:*![[Pasted image 20231208192932.png]]
Above system is *causal*.
All the places I am referencing, should lie below $y=x$ line.

*Eg:* What about $$y(t) = x(-t^2)$$Above system is *not causal*, Lets see graphs of $y=x$ and $y=-x^2$,
![[Pasted image 20231208193337.png]]*There, is a section from $[-1,0]$, In this section I am looking into the future.*
***
# Stability
We will look into this from the POV of **BIBO (Bounded Input, Bounded Output)**.