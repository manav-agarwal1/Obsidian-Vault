## Discrete time signal $\delta [n]$
$$
\delta[n] =
\begin{cases}
  1, & \text{if } n = 0, \\
  0, & \text{if } n \neq 0.
\end{cases}
$$
## Continuous time signal $\delta(t)$
$$
\delta_{bad}(t) =
\begin{cases}
  1, & \text{if } t = 0, \\
  0, & \text{if } t \neq 0.
\end{cases}
$$
Problem with $\delta_{bad}(t)$ is that it doesn't do anything. Say, If we integrate it is 0. $$\int_{-\infty}^{\infty} \delta_{bad}(t) \, dt = 0$$
So, we need to some create something more functional, and in pursuit what we actually have is not a function at all.$$
\delta(t) =
\begin{cases}
  \infty, & \text{if } t = 0, \\
  0, & \text{if } t \neq 0.
\end{cases}
$$Now, it is very misleading, we actually have a [[Generalized Function]] **and they only make sense when integrated**. They don't behave like other functions.  *Continuous time version has a very specific name = **Dirac Delta Function**.*
$$\int_{a}^{b} \delta(t) \, dt = 
\begin{cases}
  1, & \text{if } 0 \in [a,\,b], \\
  0, & \text{if } 0 \notin [a,\,b].
\end{cases}
$$
#
**What happens when there is a endpoint of 0 in interval ?**

**How to draw it?**
![[Pasted image 20231206194503.png]]
This thing is very weird and it doesn't exist in same realm as normal mathematical graphs.

**Eg:** A unit impulse function, which has 1 on $x=3$ and -2 on $x=-2$.
**Ans:** $$x(t) = \delta(t-3) - 2\cdot\delta(t+2)$$

## More on Dirac-Delta Function
![[Pasted image 20231206195452.png]]
Graph gets narrow and narrow and taller and taller, to maintain the integral.


## Simplification

![[Pasted image 20231206201924.png]]

## Sifting Property
$$
\begin{align*} 
& f(t) \cdot \delta(t-a) &&= f(a) \cdot \delta(t-a), \\ 
& \text{Integrating on both sides from } -\infty \, \text{to} \, \infty, \\ 
& \int_{-\infty}^{\infty} f(t) \cdot \delta(t-a) \,dt &&= \int_{-\infty}^{\infty} f(a) \cdot \delta(t-a) \,dt, \\ 
& &&= f(a) \int_{-\infty}^{\infty} \delta(t-a) \,dt, \\ 
& &&= f(a). 
\end{align*}
$$
This is called *sifting property*. Same thing is applicable in discrete case and it even so, comes easily as the definition there is much more clear and we have a function in place of generalized function in continuous case.
