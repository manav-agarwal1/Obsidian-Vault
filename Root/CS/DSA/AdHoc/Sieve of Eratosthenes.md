Complexity: $O(nlog(log(n)))$
- We take all number from $2$ to $n$ and mark down all their multiples as composite at each iteration.
```
sieve_of_erast(int n) {
	vector<int> prime(n+1, true);
	prime[0] = prime[1] = false;
	for (int i = 2; i*i <= m; i++) {
		if (prime[i] && i*i*1ll <= n) {
			for (int j = i*i; j <= n; j += i) {
				prime[j] = false;
				// we are not starting j from i*1 or i*2 as we have already marked those when we were running for lower i, so it would be redundant effort
			}
		}
	}
}
```
Inner loop run = $\frac{n}{i}$ times
and if we ignore the prime check then we get $$\sum_{2}^{n} \frac{n}{i} = n \sum_{2}^{n} \frac{1}{i} \tag{1}$$From [[Prime Number Theorem]] we know that if $p(n)$ is number of primes $\lt n$ then, $$\lim_{n \,\to \infty} \frac{p(n)}{\frac{n}{log(n)}} = 1$$
If we assume that $[0, n]$ is divided in slots spaced at $log(n)$ then it says that based on this average density $i-th$ prime will be $i\,ln(i)$
So, a more tighter bound for $(1)$ will be,
$$n \sum_{2}^{\frac{n}{ln(n)}} \frac{1}{i\,ln(i)}$$
For large numbers if we take integral instead of sum we will get that $ln(ln(n))$ term
So, we get the time complexity.
***
# Sieve till root
```
sieve_of_erast_til_root(int n) {
	vector<bool> prime(n+1, true);
	prime[0] = prime[1] = false;
	for (int i = 2; i*i <= n; i++) {
		if (prime[i]) {
			for (int j = i*i; j <= n; j += i) {
				prime[j] = false;
				// we are not starting j from i*1 or i*2 as we have already marked those when we were running for lower i, so it would be redundant effort
			}
		}
	}
}
```
If we reach an $i > \sqrt{n}$ then $i*i \gt n$ so, no need to mark of composites or do anything.
We can also do nothing for even numbers $\gt 2$.
