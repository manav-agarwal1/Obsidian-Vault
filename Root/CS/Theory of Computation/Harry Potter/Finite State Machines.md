# Introduction

- Also called **Finite Automaton (plural Automata)**.
- Simplest Model of Computation. It models a simple computer or a microcontroller.
	- Limited memory.
		- Finite & small
- Following $3$ describes same class or set of languages, and we call them equal in expressive power:
	- Regular languages
	- Regular expressions
	- Finite State Machines
*Eg*. 
![[Pasted image 20240202181659.png]]
Given FSM accepts all the strings starting at $a$ and ending at $d$. So, we can see that the horizontal edges are labelled with $1$ and vertical edges are labelled with $0$.
- With even number of $1$'s we stay at either $a$ or $c$, else we go for either $b$ or $d$.
- With even number of $0$'s we stay at $a$ or $b$, but with odd we go for either $c$ or $d$.
- So, all the accepted strings will have odd number of $1$'s and $0$'s.
Starting state: Always single initial state.
Accepting states: Can be more than 1, can also be $0$.
Alphabets = Symbols that label the transition edges.
***
**Finite State Machine**:
**Definition**: Defined by $5$ states.
- $M = \{Q, \Sigma, \delta, q_o, F\}$
	- $Q$ = States, **Finite** set of states.
	- $\Sigma$ = Alphabet, **Finite** set of symbols. Labels on the edges.
	- $\delta: Q \times \Sigma \to Q$ = Transition Function. The transition edges. Given a state and a symbol, it tells you which state you go to.
	- $q_0 \in Q$ = Initial State.
	- $F \subseteq Q$ = Final/Accepting States. It can be a empty set as well.
***
## Generate String
- Start at initial state.
- Take transitions at random.
- Finish in only a Accepting state.
- Gather all the labels as you traverse, and you have a string.
Now we can ask what is the set of all strings a particular FSM can generate?
***
## Accept strings
- Start in initial state
- Look at first symbol in string and transition as string characters.
- Process all the symbols.
- At the end if you end up in a Accepting state then we can accept the string. If not then reject.
Then we can ask for set of strings accepted in this manner, and that set will be the language **recognized** by the FSM.
***
- $\epsilon$ = Denotes the empty string. Only one state which is also a Accepting state, 
- $\phi$ = Denotes the empty language. FSM can have a bunch of states, but no path reaches any Accepting state.
	- $\{\epsilon\} \neq \phi$
	- $\epsilon \neq \phi$
	- If a machine accepts no language at all then it recognizes the empty language.
***
*Eg*. Any string that doesn't contains $0011$, and $\Sigma = \{0, 1\}$.
![[Pasted image 20240202181721.png]]
lets have solve for simpler problem when we have $0011$ in the string.

Then flip the states from being non-accepting to accepting and vice versa.
![[Pasted image 20240202181732.png]]
***
# Terminology
- *FSM accepts a string*
- *FSM recognizes a string*
# Notation
- $L(M)$
	- The language that $M$ recognizes.
	- The set of strings over $\{0, 1\}^*$, that contains $\dots$ as a substring.
- $\overline{L(M)}$ = Compliment of the language $L(M)$.
	- We need a universe, sometimes we don't say it explicitly but there should be a universe for this to make sense.
	- In the example shown above the universe it all the strings made of $0$ and $1$, ie; $\{0,1\}^*$.
***
*Eg* 
![[Pasted image 20240202181749.png]]
What language does the following FSM recognizes?
**Ans**: It recognizes $01$, $0^+1 = 01, 001, 0001, \dots$.
$L = \{w \, | \, w \text{ is eiher 10, or at least one 0 followed by a 1}\}$
The given FSM is correct, although there is no where to go from $d$ if you see a $1$, it goes toa a dead state and stays there. So, we just didn't show the dead state. The complete states are shown below.
![[Pasted image 20240202181803.png]]
So, the **Dead** states can be assumed are there for any missing edges.
***
- $\delta$ is a function. and formally must be defined for all possible inputs.
	- If some transitions are missing then they can be assumed to be going to a dead state. Generally, dead states can be omitted from the state-transition diagram of the FSMs.
***
# Computation

**Formal Definition**:
Let   $M = \{Q, \Sigma, \delta, q_o, F\}$
Let $w = w_1w_2\dots w_N$, be a string where $w_i \in \Sigma \forall i$.
$M$ accepts $w$, **if there is a sequence of states $r_0, r_1, r_2, r_3, \dots , r_N \in Q$ such that**
- $r_0 = q_0$
- $\delta(r_i, w_{i+1}) = r_{i+1}, for \, 0 \leq i \lt N$ = Every state is connected to next state by respective symbol in the string. 
- $r_N \in F$ 

So, a machine $M$ **recognizes** a language $A$, if $$A = \{w \, | \,  M \text{ accepts } w\}$$
**Regular language**: A language is said to be **regular** $\iff$ there is some FSM that recognizes it.
- **Intuition**:
	- FSM has very limited memory, and that contains information about states. So, their are limitation when it comes to storing information about what has happened before the state you are currently in.
	- **FSM cannot store strings**.
	- **FSM cannot count**.
	- So, these are working on similar [[Markov Property]] or, **Memoryless Property**, that only the current state is sufficient to remember what is happening.
*Eg*. A string made up of $2$ identical parts is **not part of regular** language because to know what is happening in the second part you have to remember what happened in the first part and that can require arbitrary amount of memory.
*Eg*. $0^N1^N$ is **not regular**. You have to count, and you cannot count using FSM.
***
*Eg* Binary numbers that are divisible by $3$.
This language is **regular**.
$\Sigma = \{0, 1\}$
language itself is the set of all the multiples of $3$ written in binary.
**Ans**.
As we scan binary numbers, what does each bit do?
- If we see a $0$ then it can be seen as operation of **left shift**, and it can be seen as **multiplication by $2$**.
- If we see a $1$ then it can be seen as the **left shift** followed by **addition with 1**.
So, if $$r_{i+1} = 
\begin{cases}
& 2(X), &&r_{i+1} = 0, \\
& 2(X)+1, &&r_{i+1} = 1.
\end{cases}
$$
Where $X$ is the number formed till $r_i$.
In $\mod 3 = \{0, 1, 2\}$ we have these possible values so, only $3x$ is divisible by $3$ not $3X+1$, and not $3X+2$. These will be possible states as well.
- We saw a $0$ then, we can land in one of the $3$ cases
	- $2(3X) = 3(2X)$
	- $2(3X+1) = 3(2X)+2$
	- $2(3X+2) = 3(2X+1)+1$
- We saw a $1$ then, we can land in one of the $3$ cases
	- $2(3X)+1 = 3(2X)+1$
	- $2(3X+1)+1 = 3(2X+1)$
	- $2(3X+2)+1 = 3(2X+1)+2$
![[Pasted image 20240202181821.png]]
***













**Theorem** For every **Non-Deterministic FSM** we have a **Deterministic FSM**, and vice versa.
These $2$ types of FSMs have exact same computational power.
**CATCH!!** - It can be hard to find the **Deterministic** version and it can be very large.
- *Eg*, All the strings over $/{0, 1/}$ that have $0$ in the second to last position.
***
# Non-Deterministic FSM

*Motivation*: Eg, string contains either $\dots 0100 \dots$ or $\dots 0111\dots$,
- When to start looking for the pattern?
- Which string to look for?
These are the major questions standing in the way to create a machine to solve this problem, and this can motivate why there are certain advantages in **Non determinism**.
- $P(S)$ = Power set of $S$.

***
# Deterministic FSM