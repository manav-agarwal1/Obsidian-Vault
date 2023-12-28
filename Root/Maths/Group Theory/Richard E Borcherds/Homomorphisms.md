**Def:** It is a map $f: G\to H$, where $G$ and $H$ are group and $f$ preserves multiplication.
- For any $\{a, b\} \in G$,  $f(ab)=f(a)f(b)$
	- Consequence of this is: $f(e_G) = e_H$
	- Consequence of this is: For any $a \in G$, $f(a^{-1}) = f(a)^{-1}$
It preserves the group structure.

It is called an **Isomorphism** if $f$ is a *bijection*.
It is called an **Automorphism** if $f$ is **Isomorphism** from $G \to G$ (Symmetries of groups). And set of **Automorphism** is itself a group as it is group of symmetries of something.
**Kernel of $f$** = $\{a \in G \,|\, f(a) = e_H\}$

***
*Eg:* $f(x) = e^{x}$, 
$e^{x+y} = e^xe^y$
$LHS$ = $\text{Group operation of } \mathbb{R} \text{ under } +$
$RHS$ = $\text{Group operation of } \mathbb{R}^* \text{ under multiplication}$
where, $\mathbb{R}^*$ means set of non-zero Reals.
So, we can see $f$ is a **Homomorphism**.
It is not a *Bijection*, as $e^x$ is always positive so, not *onto*.
However, it is an **Isomorphism** from $\mathbb{R}(+) \to \mathbb{R}^*(*)$. Inverse if $log$.



*Eg:* 
$$det
\begin{pmatrix}
  a & b \\
  c & d
\end{pmatrix}
$$
$det(AB) = det(A)det(B)$
So, $det$ is an **Homomorphism** from $GL_n(\mathbb{F}) \to \mathbb{F}^*$, where $\mathbb{F}$ is any field.
So, $GL_n(\mathbb{F})$ is group of invertible matrices, where elements of those matrices belong to $\mathbb{F}$.
If $n=0$, then this is trivial group and this map isn't onto anymore.
**Kernel** = $SL_n(\mathbb{F})$ = *Set of matrices with determinant 1* = Special Linear Group
**Special means determinant 1 in linear Algebra**



*Eg:* $\mathbb{Z}/4\mathbb{Z}$ = Integers modulo 4
 $(\mathbb{Z}/5\mathbb{Z})^*$ = Non-Zero Integers modulo 5 under multiplication
 ![[Pasted image 20231217023628.png]]
 These groups are **Isomorphic**.
 ![[Pasted image 20231217023734.png]]
 ![[Pasted image 20231217023854.png]] These multiplications will look same by changing values by $f$, though some reordering rows may be needed. So, its hard to use multiplication table to figure out whether the group is **Isomorphic**.
*Elements of $\mathbb{Z}/4\mathbb{Z} \cong (\mathbb{Z}/5\mathbb{Z})^*$ are **Automorphism** of $\mathbb{Z}/5\mathbb{Z}$.![[Pasted image 20231217024408.png]]
*
 


*Eg:* Map from $\mathbb{R}$ to **Circle Group** $S^1$ = $\{x, y \, | \, x^2+y^2=1\}$
![[Pasted image 20231217024604.png]]Will be group multiplication.
![[Pasted image 20231217024640.png]]

 $\theta \to (cos(\theta), sin(\theta))$
 This is our map. 
 $f(\theta_1 + \theta_2) =  f(\theta_1)f(\theta_2)$![[Pasted image 20231217025024.png]]
 **Kernel** = $\{\theta \in \mathbb{R} \, | \, cos(\theta)=1, sin(\theta)=0\}$ = *Integer multiples of $2\pi$*



*Eg:* $G$ = group of rotations of octahedron = order $24$
$H$ = $S_3$ = Permutation group of 3 points = order $6$
$3$ points in $S_3$ are going to be $3$ diagonals of octahedron. Any rotation of the octahedron will permute the $3$ diagonals.
**Kernel** = 3 rotations by 180$\degree$ about the diagonal + trivial symmetry


 


 
  
 






