---
Topic: Computer Science
---

#CS
**Algorithm**: Well defined procedure to take some inputs and produce output.
- Should focus on *Correctness*. Though not all, as there are *Probabilistic* and *Randomized* Algorithms.
- Should focus on using the resources *Efficiently*.

**Data Structure**: way to store and organize data to facilitate access, and modification.
	- *Abstract Data Type*: describe the functionality (which operations are supported)
	- *Implementation*: way to realize the functionality.


# Efficiency Analysis

- Determine function T(n) of input size n.
- Characterize rate of growth of T(n).

# Comparing order or growths

- $\log^a(n)$  grows slower than $n^b$ for all a > 0  and b > 0. *Logarithmic functions grow slower than polynomial functions.*
- $n^a$ grows slower than $b^n$ for all a > 0 and b > 1. *Polynomial functions grow slower than exponential functions.*

# Describing Algorithms

- The **Algorithm**: clear and concise.
- Proof of **Correctness**.
- Derive the runtime.

# $\mathbb{\theta}$ - Notation
 Let $g(n) : \mathbb{N} \to \mathbb{N}$ be a function. Then we have,
 $$\theta(g(n)) = \{ f(n) \,|\, \text{there exist positive constants}\, c_1, c_2, and\, n_0 \text{ such that }\, 0 \leq c_1 g(n) \leq f(n) \leq c_2 g(n) \,\, \text{for all}\, n \geq n_0\}$$

