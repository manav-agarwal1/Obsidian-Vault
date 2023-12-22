## Discrete time signal $u[n]$

$$
u[n] =
\begin{cases}
  0, & \text{if } n < 0, \\
  1, & \text{if } n \geq 0.
\end{cases}
$$

- **Eg**: A function that starts at 1 and ends at 5. $$ x[n] = u[n-1] - u[n-6] $$

## Continuous time signal $u(t)$

$$
u(t) =
\begin{cases}
  0, & \text{if } t < 0, \\
  1, & \text{if } t > 0, \\
  ?, & \text{if } t = 0.
\end{cases}
$$
*What happens at t = 0 is not fixed, some texts say it is 1, some say it is 1/2 (reason for that will be clear in [[Fourier Series]].
- **Eg:** Something that starts at 1 and ends at 4. $$x(t) = u(t-1) - u(t-4)$$
**Note:** In discrete domain at the end ie; at 6, there is nothing between 5 and 6 as it is discrete domain so function shuts off at 5, but for the second case there will be things going on between 3 and 4, as there is concept of time there in this case.

- **Eg**: Create a pyramid with start at 0 and end at 4 and peak at 2. We will use **Ramp Function** => $$r(t) = t.u(t)$$
- Coming to pyramid: $$t.u(t) - 2.(t-2).u(t-2) + (t-4).u(t-4)$$
Here, the second term cancels the slopping action of first term and we use **2x** of that so, we can start slopping down. Now, the third term is to cancel the slopping action of second term, and we only need **1x** of that as we don't want to slope back up again.