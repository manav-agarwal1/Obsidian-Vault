We have $2$ languages $A$ and $B$ and we can obtain a new languages using following operations.
- **Union**$$A \cup B = \{x \, | \, x \in A \, or \, x \in B\}$$
- **Concatenation**$$A \circ B = \{xy \, | \, x \in A \, and \, y \in B\}$$
- **Star**$$A^* =\{x_1x_2\dots x_k \, | \, k \geq 0 \text{ and each } x_i \in A\}$$
	- We can notice that $\epsilon$ is always in this set.
***
**Theorem**  *Class of **Regular Languages** is closed under **Union***.

**Proof** *Proof by **Construction***
Assume, $L_1 = L(M_1)$ and $L_2 = L(M_2)$
We need to build a $M$ that recognizes $L_1 \cup L_2$.
So, the combining of machines won't work as when both have same alphabets then our $\delta$ will be ambiguous.
We cannot rewind input so, one we looked at the inputs then we cannot relook and we cannot store a string in FSM so, we cannot run $M_1$ and $M_2$ one after another.
**Idea**:: we are going to run both these machines simultaneously, so, one state in $M$ will correspond to $2$ states - One from $M_1$ and one from $M_2$

$M_1 = \{Q_1, \Sigma_1, \delta_1, q_1, F_1\}$
$M_2 = \{Q_2, \Sigma_2, \delta_2, q_2, F_2\}$
So, $M = \{Q, \Sigma, \delta, q_o, F\}$,  where
- $Q = Q_1 \times Q_2 = \{(r_1, r_2) \, | \,  r_1 \in Q_1 \, and \, r_2 \in Q_2\}$ So, if $x \in Q_1$ and $1 \in Q_2$ then one possible state can be $x1$.
- $\Sigma = \Sigma_1 \cup \Sigma_2$
- $\delta((r_1, r_2), a) = (\delta_1(r_1, a), \delta_2(r_2, b))$
- $q_0 = (q_1, q_2)$
- $F = \{(r_1, r_2) \, | \, r_1 \in F_1 \,\mathbf{or}\, r_2 \in F_2\}$ **CAUTION!!**, we have a **OR** there so, if $x$ is accepting state in $Q_1$ and we have $3$ in $Q_2$ as not accepting state then $x1$ will be accepting state.
***
**Theorem**  *Class of **Regular Languages** is closed under **Concatenation***.

**Proof**: [[Non Determinism]] is required.
***
