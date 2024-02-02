**Determinism** = Given current state we will know what the next state will be.
- Only $1$ unique next state
- No choices
- No randomness (Perfectly **replicable**)
- No oracles.
- No cheating (No errors or malfunctions)

**Normal computers are deterministic**, though they take random inputs like random keystrokes based on timing, sometimes random errors disturb repeatability. We are moving towards highly complex machines which are further than **determinism**.
***
# Nondeterminism

**Given the current state there might be multiple next states**.
- The next state is chosen at random
- All the next states are chosen in parallel and pursued simultaneously, [[Quantum Computers]].
***
# Abbreviations

- **FSM/DFA** = Deterministic Finite State Automaton
- **NFA** = Nondeterministic Finite State Automaton
***
# NFA allows :
- In non deterministic world we can allow multiple edges coming out of a single state, for a given alphabet.
- **Epsilon Edges** = Can take $\epsilon$ edge without scanning a symbol.
- We don't need a dead state here, we can simply say no possible choice. Getting stuck means rejected though.
***
*Eg* All strings that contains $011110$.
![[Pasted image 20240202181846.png]]
***
**All we need is one way to reach accepted state**. Then we say the NFA accepts the strings.
When we have many choices, then we can do following equivalent things:
- Try all them all.
- Make the right choice at each point
***
 *Eg*
![[Pasted image 20240202181911.png]]
**Computation tree** or **choice tree** of above example
![[Pasted image 20240202181921.png]]
***

