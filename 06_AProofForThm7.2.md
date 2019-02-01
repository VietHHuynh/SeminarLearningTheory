---
title: "Proof of Theorem 7.2"
---

## A Proof Proposal for Theorem 7.2

**Theorem 7.2:**
A hypothesis class $\mathcal{H}$ of binary classifiers is nonuniformly learnable if and only if it is a countable union of agnostic PAC learnable hypothesis classes.

**Proof Proposal:** 

"$\Leftarrow$" as in the book.

"$\Rightarrow$" 
Assume that $\mathcal{H}$ is nonuniform learnable using some algorithm $A$.
For every $n \in \mathbb{N}$ let 

$ \mathcal{H}\_{n} := \\{ h \in \mathcal{H} : m\_{\mathcal{H}}^{NUL} (1/10, 1/10, h) \leq n \\} .$

It follows that $\mathcal{H} = \bigcup\_{n \in \mathbb{N}} \mathcal{H}\_{n}$.

We prove the "$\Rightarrow$" claim by contradiction. 
I.e., assume that $\mathcal{H}\_{n}$ is not APAC learnable then we find a contradiction to its definition:

Suppose $\mathcal{H}\_{n}$ is not APAC learnable. 
Then, by the fundamental Theorem (Thm. 6.7) $\mathcal{H}\_{n}$ has infinite VC-dimension.
(Note, that this implies that the domain $\mathcal{X}$, on which $\mathcal{H}\_{n}$ and $\mathcal{H}$ operate must be infinite, as well).
Thus, $\mathcal{H}\_{n}$ shatters sets of size $n'$ for all $n' \in \mathbb{N}$.
$A$ is a learning algorithm for the class of binary classificators with $0-1$-loss.
Thus, for any $n'$ the No-Free-Lunch Theorem (Thm. 5.1) holds with respect to some $h' \in \mathcal{H}\_{n}$.
(In particular, Thm. 5.1 does not require $A$ to output anything more specific than a function $f: \mathcal{X} \to \\{ 0,1 \\} $.)

That is:

$ \forall n' \in \mathbb{N} \\ \exists $ a distribution $D$ that is realizable by $\mathcal{H}\_{n}$ and $\exists h' \in \mathcal{H}\_{n}$ s.t. with probability $ \geq 1/7$ over the choice of $ S \sim D^{n'}$ it holds that $L\_{D} (A(S)) \geq 1/8 = L\_{D} (h') + 1/8$. 

However, by definition of $\mathcal{H}\_{n}$ we have $\forall h\in \mathcal{H}\_{n} : m\_{\mathcal{H}}^{NUL} (1/10, 1/10, h) \leq n$.
That is, $ \forall D \\ \forall h \in \mathcal{H}\_{n} : L\_{D} (A(S)) \leq L\_{D}(h) + 1/10 $ with probability $\geq 9/10$ over the choice of $S \sim D^n$.

Considering the case $n' = n$ yields the desired contradiction.
Hence, $\mathcal{H}\_{n}$ must be agnostic PAC learnable. 

## Comments
 * Looks reasonable to me. Just a small suggestion: As you argue anyway with $L\_{D} (h') + 1/8$ and $L\_{D}(h) + 1/10$ (and not only with 1/8 and 1/10), we could drop the realizability assumption completely and directly argue for all $D$. In my opinion, this would make the proof even a little simpler.
