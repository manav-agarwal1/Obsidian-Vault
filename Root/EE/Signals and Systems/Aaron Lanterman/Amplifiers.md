Let given **gain**, $k$. But Amplifiers have limited **Bandwidth**. Given gain is at **DC**.
Model:
$H_1(s) = \frac{k\omega_c}{s + \omega_c}$
Let, $k = 200,000$, and $f_c = 6 Hz$
In *feedback*, we have $\beta$.
![[Pasted image 20240123075317.png]]
Now using, [[Black's Feedback Formula]].
$H(s) = \frac{k\omega_c}{s + (1 + \beta k)\omega_c}$
Earlier **Bandwidth** was low, so, using **negative feedback**, we improved the **Bandwidth**.
$H(j0) = \frac{1}{1+\beta k} \approx \frac{1}{\beta}, \text{ for large } k$
But, we lost **DC Gain**.
$k$ and **Amplifier** vary with temperature so, we can choose $\beta$ with components that don't vary with temperature and compensate other variations.
***
