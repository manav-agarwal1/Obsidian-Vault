- **Predicates**$$f : \text{Domain} \to \{0,1\}$$Domain can be infinite or finite.
- **Property** = **Predicates** that take *one argument*.
- **Relation** = **Predicates** that take *multiple argument*.
	- *Reflexive*
	- *Symmetric*
	- *Transitive*
- If we have a **directed edge** between $2$ vertices in a graph then those $2$ vertices can be said to have a **Binary Relation**.
- $\Sigma$: used to symbolize set of *alphabets*. Always a *finite* set.
- **Strings** = sequence of *alphabets*.
	- $\epsilon$ = symbolize and *empty string*.
	- $|\dots|$ = used to denote length of string.
	- `xy` = concatenation
	- $x^R$ = Reverse of a string
- **Language** = set of **strings**. Can be *finite* or *infinite*.
	- The **empty language** $\phi$ = empty set. It doesn't even contains $\epsilon$, so these are different concepts.
	- Describing language:
		- **Enumeration** = Listing out the all the elements. Only suggested to use in *finite* case.
		- **Regular Expression**
		- **Context-Free Grammars** = Powerful but cannot describe all the *languages*.
			- It is king of map, eg.  $S \to dTd$ and $T \to TT | aTb | \epsilon$
		- **Set Notation** = eg $\{x | \text{ conditions }\}$
- **Proofs**:
	- **By Construction**
	- **By Contradiction**
	- **By Induction**
		- **Structural Induction** = Prove it is true for all the ancestors of $x$ if it is true for $x$, Hence, it is true for *root*.




