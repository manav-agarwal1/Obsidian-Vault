$X(s)$ represents the [[Laplace Transforms]] of $x(t)$
# Final Value Theorem
$$
x(\infty) = \lim_{t \to \infty} x(t) = \lim_{s \to 0} s\cdot X(s)
$$
***
# Initial Value Theorem
$$
x(0^+) = \lim_{t \to 0^+} x(t) = \lim_{s \to \infty} s \cdot X(s)
$$
***
Usually as we have seen in examples of [[Laplace Transforms]], and in many engineering applications we will have $x(0^+) = x(0)$, so, things are usually nice around **Initial Value Theorem**.
**WARNING!!!** - ***And both these theorems are valid only if the $\lim$ exists*.**
***
# Danger

*Eg*. Let, $$X(s) = \frac{3}{s^2 + 9}$$
And, $x(\infty)$ from **Final Value Theorem**, says it is $0$.
But what is we take **Inverse Laplace Theorem**, it is $x(t) = sin(3t) u(t)$, and $x(\infty) \neq 0$, but it is ever going, so, the result we got is wrong.

*Eg*. $$x(t) = sin(\frac{1}{t})$$
As, I approach $0$, then things got weird. I mean here we don't have **Laplace Transform** anyway.
***
We input $x(t) = u(t)$ for the three types of filters discussed in [[Canonical Second Order Filters]]. We will calculate limiting cases using above theorems.
- Step Response from **LPF**:
	- $y_{LP}(0) = \lim_{s \to \infty} s(\frac{1}{s} H_{LP}(s)) = 0$
	- $y_{LP}(\infty) = \lim_{s \to 0} s(\frac{1}{s} H_{LP}(s)) = 1$
- Step Response from **BPF**:
	- $y_{BP}(0) = \lim_{s \to \infty} s(\frac{1}{s} H_{BP}(s)) = 0$
	- $y_{BP}(\infty) = \lim_{s \to 0} s(\frac{1}{s} H_{BP}(s)) = 0$
- Step Response from **HPF**:
	- $y_{HP}(0) = \lim_{s \to \infty} s(\frac{1}{s} H_{HP}(s)) = 1$
	- $y_{HP}(\infty) = \lim_{s \to 0} s(\frac{1}{s} H_{HP}(s)) = 0$
This $\frac{1}{s}$ arises from, the **Laplace Transform** of $u(t)$ as we will convolve it with **Impulse Response** system but in **Laplace** domain that will be multiplied with the **Frequency Response** of system.
***
