[Video Link](https://www.youtube.com/watch?v=Xz7_QJ-sIVk)
**Motivation**: For groups $G$ and $H$ **direct product** is defined by $G\times H$, such that, $$(g_1, h_1)*(g_2, h_2) = (g_1g_2, h_1h_2)$$Now, here the `*` is the new operation and $g_1g_2$ are following $G$ operation and $h_1h_2$ following $H$ operation. *We abused notation here*.

We have a trivial **Homomorphism**:
*Inclusion maps, they are **injective***.
- $\iota_G: G \to G \times H$, $g \to (g, e_H)$
- $\iota_H: H \to G \times H$, $h \to (e_G, h)$
*Natural Projection maps*. *If we do a **Quotient** then we get similar maps, but these are just natural projections*.
- $\pi_G: G\times H \to G$, $(g,h) \to g$
- $\pi_H: G\times H \to H$, $(g,h) \to h$
*Observations*:
- $im(\iota_G) = ker(\pi_H)$
- $im(\iota_H) = ker(\pi_G)$
- $\pi_G \circ I_G = e_G$
- $\pi_H \circ I_H = e_H$
  This **Direct Product** contains $2$ subgroups and both are **kernel** of some **homomorphisms**. And, those maps are from $G \times H \to some\, X$, hence, by result proved in [[Normal Subgroup]], both of them are **normal** in $G\times H$
- $G \cong im(\iota_G) = ker(\pi_H) = \widetilde{G}$
	- Think of $\widetilde{G}$ as $(g, e_H)$ sitting inside $G \times H$.
- $H \cong im(\iota_H) = ker(\pi_G) = \widetilde{H}$
- $\widetilde{G} \cap \widetilde{H} = \{(e_G, e_h)\}$
- $\widetilde{G}\widetilde{H} = G \times H$
So, from these observations we can have this following definition:
***
**Definition**: Let $G$ be a group with subgroups $H$ and $K$, such that If $H$ is **normal** we call $G$ as [[Semidirect Product]] of $H$ and $K$ ($H\ \cap K = {e}$), and if $K$ is also **Normal** we call $G$ as **Internal Direct Product** of $H$ and $K$.

**Proposition**: If $G$ is **semidirect product** of $H$ and $K$, then $\forall \, g \in G \, \exists\, \text{unique } h \in H, k \in K$ such that $g = hk$.
**Proof**: Suppose $h_1k_1 = h_2k_2$, then $h_2^{-1}h_1 = k_2k_1^{-1}$, and since we know $H \cap K = \{e\}$.

**Theorem**: If $G$ is **internal direct product** of $H$ and $K$ then $G \cong H \times K$ (**Direct product or external direct product**).
**Proof**: Let, $\phi: G \to H \times K$, given by $\phi(g = hk) \to (h, k)$, as we have showed uniqueness for this in above preposition we can say it is a **bijection**.
Both $H$ and $K$ are **normal subgroups**.
So,  **commutator** of $[k, h] = khk^{-1}h^{-1} = (khk^{-1})h^{-1} = k(hk^{-1}h^{-1})$, So, the brackets are **conjugate action** on a **normal subgroup**. So, this **commutator** lies inside both $H$ and $K$ ie; $H \cap K = {e}$.
So, this **commutator** is **identity** and $H$ and $K$ commute with each other.
$\phi(g_1g_2) = \phi(h_1k_1h_2k_2) = \phi(h_1h_2k_1k_2) = (h_1h_2, k_1k_2) = (h_1, k_1) * (h_2, k_2) = \phi(g_1) * \phi(g_2)$
So, it is a **homomorphic bijective** map hence, an **isomorphism**.
***
**Second Isomorphism Theorem**:: Let $G$ be a group and $H$ and $N$ be subgroups of $G$ such that $N$ is a **Normal Subgroup** of $G$ then set $HN = \{hn \, | \, h \in H, n \in N\}$ is a subgroup of $G$, and the following hold:
- $H \cap N \stackrel{\Delta}{\_} G$
- $H / (H \cap N) \cong HN/N$
**Proof**: $H \cap N \stackrel{\Delta}{\_} G$ is trivial since, $N \stackrel{\Delta}{\_} G$.
Define $\phi: H \to HN/N$ by $\phi(h) = Nh$
- $\phi(h_1h_2) = Nh_1h_2 = Nh_1 \cdot Nh_2 = \phi(h_1) \cdot \phi(h_2)$
	- $N$ is **normal subgroup** so, coset multiplication is well defined and this fact is used.
	- $\therefore \, \phi$ is a **Homomorphism**.
- Take any $Nx \in HN/N$, this means $x \in HN$ so, $x = hn, h \in H, n \in N$.
	- $xh^{-1} = hnh^{-1} \in N$, since **conjugation** fix **Normal** subgroups.
	- Then $Nx = Nh \implies \phi(h) = Nx$, so the map is **surjection**.
Now using [[First Isomorphism Theorem]],
$H/ker(\phi) \cong HN/N$
$ker(\phi) = \{h \in H \,|\, \phi(h) = e_{HN/N}\} = \{h \in H\, | \, Nh = N\} = \{h \in H \, | \, h \in K\} = H \cap K$So, our theorem is proved.
***
**Theorem**: If $G$ is a **semidirect product** of $H$ and $K$ then due to **second isomorphism theorem** $K \cong K/(H \cap K) \cong KH/H \cong HK/K \cong G/H$.
If $H$ is **Normal** and we know $G$ is **semidirect product** of $H$ and $K$ then $K$ is determined.
***
**Extension** problem asks me to find all the possible **extension** of $H$ by $K$.
By **extension** we mean::
- $G$ is said to be an **extension** of $H$ by $K$ if, $G$ contains $H$ as a **Normal subgroup**, and additionally $G/H \cong K$.
***
**Exact Sequence**: $$\dots \to G_{i-1} \xrightarrow{\phi_i} G_i\xrightarrow{\phi_{i+1}} \dots$$
This thing is **exact** at $G_i$ if $ker(\phi_{i+1}) = Im(\phi_i)$.
Furthermore, whole sequence is **exact** if it is **exact** $\forall \, i$.
**So, everything coming from $\phi_i$ to $G_i$ is killed by $\phi_{i+1}$.**
***
**Short Exact Sequence**
$$ 0 \to N \xrightarrow{\iota} G \xrightarrow{\pi} H \to 0$$
If $\iota$ be the **Inclusion Map**, and $N$ be **Normal Subgroup** of $G$ and $\pi$ be the **Quotient Map**, and $H = G/N$.
$$ 0 \to N \xrightarrow{\iota} G \xrightarrow{\pi} G/N\to 0$$
This *archetypical* example of **short exact sequences**.
***
[Video-2 Link](https://www.youtube.com/watch?v=tFmbJEaEx3Q)












