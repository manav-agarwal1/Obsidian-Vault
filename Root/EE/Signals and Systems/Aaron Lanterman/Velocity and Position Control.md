# Velocity Control
![[Pasted image 20240123101348.png]]
Here, we shifted the pole to left from $-a$ to $-a-k_pk$, which will speed up the system towards **steady state response**.

This $H_{CL}(s) \lt 1$ even **asymptotically**, and only way to get better is to push $K_p \to \infty$, which will blow up system.
So, we will use a modification in $G_c(s)$, 
![[Pasted image 20240123102051.png]]
This is called **Integral Proportional Controller**, as dividing by $s$ in **Laplace Domain**, is **Integrating**, in time domain, [[Laplace Transforms - Properties and Operations]]. So, we are following one term for **Integral** as well.
This version gives us better **Asymptotical Response**.
We generally don't have any information about $a$ and $k$, so, controlling location of **poles** is done by trial and error. These parameters will also change with the lifetime of system operation.
***
# Position Control
We can now thing of input as **Velocity** instead of **Acceleration**, and we get **Position**.
![[Pasted image 20240123110234.png]]
We have divided $G_p(s)$ by $s$, so we in previous example just integrating one more time, to get **position**.
This **asymptotically** approach $1$ better.
Say we don't have $s$ in $G_p(s)$ then we can do it in $G_c(s)$.
In above, I have an $a$ in denominator so, I cannot change that. So, I have no control of **Poles**.
Solution is to add a **Derivative** term.
![[Pasted image 20240123142750.png]]
Now, I can use $K_D$ to control the coefficient of $s$.
***
- **Proportional** term = Lets the system track errors at present.
- **Integral** term = Lets the system track errors from the past.
- **Derivative** term = Lets the system contemplate what can go wrong in the future. It itself is dangerous. Noise can be a problem, both analog and digitally. So, it is divided by some **pole** that is far away, to take care of **high frequency** noise.
***

