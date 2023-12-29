![[Pasted image 20231212175032.png]]
We send $s(t)$ to saucer and whatever reflected signal we get back we convolve it with Matched Filter and say, we get the result to be the red waveform above, which is like that due to presence of noise.

Now, depending on where the saucer is the graph should have a triangle like that as that part will look like the autocorrelation of $s(t)$.

But, say we have 2 saucers then we might have 2 triangles overlapping and we might not be able to tell the difference.
![[Pasted image 20231212175333.png]]
This idea is called **resolution** of a RADAR or SONAR system.
*So, we can try some different kind of signal as $s(t) with some added complexity.*
Lets $s(t)$ be this, ![[Pasted image 20231212183357.png]]
$R_{ss}(t) = (1, 1, 1, -1, 1) *(1, -1, 1, 1, 1)$![[Pasted image 20231212183546.png]]
As, autocorrelation is symmetric and peaks at origin.
So, the intersection on presence of two saucers case is handled very well here, ![[Pasted image 20231212183742.png]]

- We can also select a unit long pulse, but that *doesn't put a lot of energy on the target.* But in RADAR we want to **maximize the energy we put on the target** to improve **signal to noise ration**.
- So, if we take a long pulse then that puts a lot of energy on target but have mediocre resolution.
- TRADEOFF: **Resolution vs Energy on Target (Signal to Noise Ratio)** 
- So, waveform like we have in images is good as it has narrow peaks but puts a lot of energy on target. This trick is called **Pulse Compression**. The one we are using in **Length-5 Barker Code**.![[Pasted image 20231212184439.png]]
***
