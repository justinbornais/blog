+++ 
date = 2024-09-24T15:11:28-04:00
title = "COMP-2310 - List of All Theorems"
description = ""
slug = ""
authors = ['Justin Bornais']
tags = ['comp-2310']
categories = []
externalLink = ""
series = []
+++

<style>.line { padding: 0 1em; }</style>

In COMP2310, you will come across a wide array of theorems. This post contains a list of all the theorems discussed in the course that may be useful.

## First-Order Propositional Logic
### Chapter 1
**Theorem 1.7.1:** A wff $\alpha$ is a theorem iff $\alpha$ is a tautology.

**Theorem 1.7.2**\
<span class="line">i.</span> $\vdash \neg false \Leftrightarrow true$\
<span class="line">&nbsp;&nbsp;&nbsp;</span>$\vdash \neg true \Leftrightarrow false$\
<span class="line">ii.</span> $\vdash (\alpha \Leftrightarrow \beta) \Leftrightarrow (\beta \Leftrightarrow \alpha)$\
<span class="line">iii.</span> $\vdash (\alpha \Leftrightarrow \beta) \Leftrightarrow (\neg \alpha \Leftrightarrow \neg \beta)$\
<span class="line">iv.</span> $\vdash (\alpha \Leftrightarrow \beta) \land (\beta \Leftrightarrow \gamma) \Rightarrow (\alpha \Leftrightarrow \gamma)$\
<span class="line">v.</span> $\vdash (\alpha \Rightarrow (\beta \Rightarrow \gamma)) \Leftrightarrow (\alpha \land \beta \Rightarrow \gamma)$

### Chapter 2
A **first-order theory** is a first-order-logic with a specific collection of constnat, function and predicate symbols, augmented with a collection (possibly empty) of axioms called ***proper axioms***.

**Axioms of equality:** A ***first-order theory with equality*** is a first-order theory which includes a two-argument predicate, $E(x,y)$, customarily written as $x=y$, for which the following axioms hold:

<span class="line">**A1.** (reflexivity)</span> $\vdash (\forall x)(x = x)$\
<span class="line">**A2.** (symmetricity)</span> $\vdash (\forall x)(\forall y)(x = y \Rightarrow y = x)$\
<span class="line">**A3.** (transitivity)</span> $\vdash (\forall x)(\forall y)(\forall z)((x = y) \land (y = z) \Rightarrow x = z)$\

<span class="line">**A4.** (substitutivity of functions)</span>\
<span class="line"></span>For every $n$-argument function $f^n$ and for each $i$, $1 \leq i \leq n$, 
$$
\vdash (\forall x)(\forall y)(\forall z_1) \cdots (\forall z_{i-1})(\forall z_{i+1}) \cdots (\forall z_n) \\\\
(x = y \Rightarrow (f^n(z_1, \dots, z_{i-1}, x, z_{i+1}, \dots, z_n) = f^n(z_1, \dots, z_{i-1}, y, z_{i+1}, \dots, z_n)))
$$

<span class="line">**A5.** (substitutivity of predicates)</span>
<span class="line"></span>For every $n$-argument predicate $P^n$ (other than $=$) and for each $i$, $1 \leq i \leq n$, 
$$
\vdash (\forall x)(\forall y)(\forall z_1) \cdots (\forall z_{i-1})(\forall z_{i+1}) \cdots (\forall z_n) \\\\
(x = y \Rightarrow (P^n(z_1, \dots, z_{i-1}, x, z_{i+1}, \dots, z_n) \Rightarrow P^n(z_1, \dots, z_{i-1}, y, z_{i+1}, \dots, z_n)))
$$

The notation $x \neq y$ denotes $\sim (x = y)$.

##### **Sub**$_{s=t}$ (Substitutivity of $=$) $\qquad\large \frac{s=t,\alpha(s)}{\alpha(t)}\quad (\alpha(s) \text{ is free for } t)\normalsize$

--- 
## Set Theory
### Chapter 3

**Principle of Extension:** $A = B \iff (\forall x)(x \in A \iff x \in B)$

**I3λ:** $\alpha \land \beta, \alpha \Rightarrow \gamma \land \alpha \beta$

**I3ν:** $\alpha \lor \beta, \alpha \Rightarrow \gamma \lor \alpha \beta$

**Lemma 3.2.1:** Let $ A $, $ B $, $ C $ be sets
  1. $ A = A $
  2. if $ A = B $, then $ B = A $
  3. if $ A = B $ and $ B = C $, then $ A = C $

**Lemma 3.2.2:** $ A \neq B \iff (\exists x)(x \in A \land x \notin B) \lor (\exists x)(x \notin A \land x \in B) $

**Corollary 3.2.2.1:** Let $ A $ and $ B $ be sets  
$ (\exists x)(x \in A \land x \notin B) \Rightarrow A \neq B $

**SUBSET:** Let $ A $ and $ B $ be two sets  
$ A \subseteq B \iff (\forall x)(x \in A \Rightarrow x \in B) $

**PROPER SUBSET:**  
$ A \subset B $ if $ A \subseteq B $ and $ A \neq B $

**Lemma 3.2.3:** Let $ A $, $ B $, $ C $ be sets
  1. $ A \subseteq A $
  2. if $ A \subseteq B $ and $ B \subseteq A $, then $ A = B $
  3. if $ A \subseteq B $ and $ B \subseteq C $, then $ A \subseteq C $

**Lemma 3.2.4:** if $ A = B $, then $ (A \subseteq B) \land (B \subseteq A) $

**Lemma 3.2.5:** $ A \neq B \iff (\exists x)(x \in A \land x \notin B) $

**Lemma 3.2.6:** if $ A \subset B $, then $ (\exists x)(x \in B \land x \notin A) $

**FE7ε:** $ \sim (\forall x \in X) S(x) \equiv (\exists x \in X) \sim S(x) $

**FE8ε:** $ \sim (\exists x \in X) S(x) \equiv (\forall x \in X) \sim S(x) $

**Principle of Specification:**  
For every set $ A $ and every formula $ S(x) $, there exists a set $ B $ whose elements are those of $ A $ for which $ S(x) $ is true.
$$ \{x \mid x \in A \land S(x)\} \text{ or } \{x \in A \mid S(x)\} $$

