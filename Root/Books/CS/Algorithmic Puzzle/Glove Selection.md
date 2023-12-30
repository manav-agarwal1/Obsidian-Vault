10 pairs = 5 black + 3 brown + 2 gray.
Selection at random and check after its made.
1. At least one pair
2. At least one pair of each color.

**Solution**:
$\# gloves = ?$
bl = 10
br = 6
g = 4
*Major pitfall*: Gloves are different for right and left hand, a matching pair will have same color right and left hand glove
1. 11, as if I take 10 then worst case it could be all right hand (or left hand) different colors but if I take 11 then by **Pigeonhole principle**, I am bound to get atleast one pair. $\frac{bl}{2} + \frac{br}{2} + \frac{g}{2} + 1$.
2. 19, So, assume after 11 we got pair for bl, now worst case all bl comes next, that brings total to 15, then at 16 I get br pair, and again by same logic I pick up 2 more, to 18 and at 19 I achieve desired state. 
```
int a = min({bl, br, g});
int res = 0;
for (int x: {bl, br, g}) {
	if (x != a)
		res += x;
}
res += (a/2) + 1;
```
