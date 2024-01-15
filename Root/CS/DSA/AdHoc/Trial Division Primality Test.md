Divide $n$ by all integers from $2, 3, \dots, \sqrt n$, and skipping the even ones. This is order of $\sqrt n$.
If $n$ can be encoded using binary strings then we need $\beta$ bits where $$\beta = \lceil lg(n+1) \rceil$$So, $\sqrt n = \Theta(2^{\beta/2})$.
$\therefore \,$ this method works fine for small $n$.