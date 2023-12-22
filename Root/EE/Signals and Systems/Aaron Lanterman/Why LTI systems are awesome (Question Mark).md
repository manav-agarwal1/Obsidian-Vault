- **Impulse Response**, fully characterizes the behavior of the system.
*Eg:*
![[Pasted image 20231208195005.png]]
![[Pasted image 20231208195108.png]]
*In the case when input is not at 0, we are using time-invariance. And, linearity is used for scaling part. And, we add as we have superposition.*![[Pasted image 20231208195336.png]]
General idea, ![[Pasted image 20231208195648.png]]
This new sign is of **convolution.** *Though convolution is doing something to the entire function, so, you can't just plug in some n and do something to **input signal and impulse response**. Convolution is done to them both, then whatever you receive can be plugged in with values and get values from.*
**Convolution is commutative.**
- LTI system, can't create new frequencies, so, whatever frequencies you feed in you will get out.![[Pasted image 20231208200359.png]]
***
**Continuous Case**
![[Pasted image 20231208200506.png]]
![[Pasted image 20231208200633.png]]
***
# Discrete vs Continuous domain
![[Pasted image 20231209181928.png]]
![[Pasted image 20231209182326.png]]
Inverse transforms allow us to write the time domain signal as the sum of complex sinusoids and we know how to these sinusoids respond to LTI systems so, we can figure out the output.
![[Pasted image 20231209182515.png]]
The coefficient of $e^{j\omega t}$, are the discrete time and continuous time fourier transforms respectively.
**Convolution in time domain => multiplication in frequency domain.**
*Note: **Complex Exponentials** are the eigen functions of the system and **Frequency response** is the eigen value.*
***
We can also do same thing with **wavelets**, like we do with **Complex Exponentials.**
***
You

I am not getting feel of some technical stuff so, don't bore with some equation and make me lost, talk straight and give me intuition. If I have a linear and time invariant system and plug in a frequency domain signal basically, an e^(jwt) I get H(jw)e^(jwt). Extra H term, now this system cannot generate frequency so frequency remains the same but why do I get the H term


ChatGPT

Sure, let's break it down in a straightforward way.

Imagine you have a system, and you're sending in a signal that varies with time like ����ejwt. This signal has a frequency component �w (omega), and the system you're passing it through is linear and time-invariant.

Now, when you input this signal into the system, what comes out is �(��)����H(jw)ejwt. Let's break down the terms:

1. **����ejwt**: This is your input signal. It represents a signal that varies with time, and �w is its frequency. This is the signal you're sending into the system.
    
2. **�(��)H(jw)**: This is the system's response to the specific frequency �w in your input signal. It's like a "filter" that affects different frequencies differently. This term tells you how the system modifies the amplitude and phase of your input signal at the specific frequency �w.
    

So, when you look at the output �(��)����H(jw)ejwt, you're essentially getting your original signal ����ejwt back, but the amplitude and phase might be changed due to the system's characteristics at that particular frequency �w.

The system doesn't "generate" frequency; it influences how the input frequency behaves. The �(��)H(jw) term represents the system's behavior at that specific frequency �w. If �(��)H(jw) is a simple number (no complex part), it means the system doesn't affect the amplitude and phase of that frequency much. If �(��)H(jw) is more complex, it means the system is doing more complicated things to that frequency.

So, in short, the �(��)H(jw) term describes how your system responds to the specific frequency in your input signal without changing the frequency itself.