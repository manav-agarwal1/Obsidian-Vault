*Eg*: let $x(t) = cos(\omega_0)t$
then $Y(s) = H(s)\frac{s}{s^2 + \omega_0^2}$.
![[Pasted image 20240104163219.png]]
![[Pasted image 20240104163325.png]]
In purple color we are talking about the **Fourier Transform** case. So, here due to $u(t)$ out `cosine` it that it starts at particular point, and we have system **poles** term sitting here, rest of it is same in both cases. If system is **BIBO** stable then system **pole** terms will decay to $0$ then in that case the sinusoids will be **steady state** output. So, *The ideas developed earlier are the **steady state** response for **BIBO** stable*. Now, we can also have initial condition here but for **BIBO** stable system terms coming from that too will be part of **transient response**.
***
You, can get **Fourier Transform** from **Laplace Transform** evaluating it at $s = j\omega$, when we have Imaginary axis is part of *Region of Convergence*.
***


