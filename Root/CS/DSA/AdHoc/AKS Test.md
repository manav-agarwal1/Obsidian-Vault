Very similar to [[Fermat's Little Theorem]]
[This is a full proof test](https://www.youtube.com/watch?v=HvMSRWTE2mI)
# Method
Say we have a number $p$ then we do $(x-1)^p - (x^p - 1)$ If all coefficients of this polynomial are divisible by $p$ then $p$ is prime.

# To make it faster:
$(x - a)^p - (x^p - a) = p(\dots) + (x^r-1)(\dots)$
For this version we test a few candidates for $a$.
