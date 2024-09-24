+++ 
date = 2023-10-04T17:44:31-04:00
title = "COMP-2310 Chaper 2 - First-Order Logic Overview"
description = ""
slug = ""
authors = ['Justin Bornais']
tags = ['comp-2310']
categories = []
externalLink = ""
series = []
+++

First-order logic is essentially an extension of propositional logic. Thus, the same equivalences and inference rules applies in FOL. However, FOL is intended to expand on propositional logic by including functions. Here's what I mean:

- If I wanted to say "John goes to the movies", "Sam goes to the movies", "Alex goes to the movies", I could use $J$, $S$ and $A$ to represent John/Sam/Alex (respectively) going to the movies.
- However, instead, what if I defined a function $M(x)$ for any person $x$ where $M(x) = x\\;goes\\;to\\;the\\;movies$?
- That way, I could have $M(j)$, $M(s)$, $M(a)$ for John/Sam/Alex (respectively) going to the movies. These are called **predicates**.
- What makes this even better is I can have an expression for "Everyone goes to the movies": $(\forall x)M(x)$ or "There exists someone who goes to the movies": $(\exists x)M(x)$.
- The $\forall$ and $\exists$ operators are called **quantifiers**.

# New Equivalences and Inference Rules

FE1. $(\forall x)\alpha(x) \equiv (\forall y)\alpha(y) \quad (\alpha(x) \text{ does not contain } y)$\
FE2. $(\exists x)\alpha(x) \equiv (\exists y)\alpha(y) \quad (\alpha(x) \text{ does not contain } y)$\
FE3. $(\forall x)\alpha(x) \lor \beta \equiv (\forall x)(\alpha(x) \lor \beta) \quad (\beta \text{ contains no free occurrence of } x)$\
FE4. $(\exists x)\alpha(x) \lor \beta \equiv (\exists x)(\alpha(x) \lor \beta) \quad (\beta \text{ contains no free occurrence of } x)$\
FE5. $(\forall x)\alpha(x) \land \beta \equiv (\forall x)(\alpha(x) \land \beta) \quad (\beta \text{ contains no free occurrence of } x)$\
FE6. $(\exists x)\alpha(x) \land \beta \equiv (\exists x)(\alpha(x) \land \beta) \quad (\beta \text{ contains no free occurrence of } x)$\
FE7. $\sim (\forall x)\alpha(x) \equiv (\exists x)\sim \alpha(x)$\
FE8. $\sim (\exists x)\alpha(x) \equiv (\forall x)\sim \alpha(x)$\
FE9. $(\forall x)\alpha(x) \land (\forall x)\beta(x) \equiv (\forall x)(\alpha(x) \land \beta(x))$\
FE10. $(\exists x)\alpha(x) \lor (\exists x)\beta(x) \equiv (\exists x)(\alpha(x) \lor \beta(x))$

**Gen: Generalization**\
$\frac{\alpha(x)}{(\forall x)\alpha(x)}\quad x \text{ is a variable}$

**UI: Universal Instantiation**\
$\frac{(\forall x)\alpha(x)}{\alpha(t)}\quad\alpha(x) \text{ is free for } t \text{ (} t \text{ is a variable or constant)}$\
$\text {where }\alpha(t) \text{ results from } \alpha(x) \text{ after all free occurrences of x in } \alpha(x) \text{ are replaced by } t$

**EQ: Existential Quantification**\
$\frac{\alpha(t)}{(\exists x)\alpha(x)}\quad\alpha(x) \text{ is free for } t \text{ (} t \text{ is a variable or constant)}$\
$\text {where }\alpha(x) \text{ results from } \alpha(t) \text{ after some (may be all) free occurences of t in } \alpha(t) \text{ are replaced by } x$

**EI: Existential Instantiation**\
$\frac{(\exists x)\alpha(x)}{\alpha(c)}\quad c\text{ is a constant}$

{{< notice note >}}
The restriction "$\alpha(x)$ does not contain $y$" on **FE1** and **FE2** can be illustrated in the following way:

1\. $(\forall x)(p(x)\land q(y))\quad$ from $\Gamma$\
2\. $(\forall y)(p(y)\land q(y))\quad$ 1, FE1

Line 2 is invalid, since the expression contains a predicate that contains $y$. Now I quantified $y$ in $q(y)$, which is nonsensical.
{{< /notice >}}

# Free Variables
In the definition of the above equivalences and inference rules, you saw the term *free occurrence* or *free variable*. A **free variable** is simply a variable that is not quantified. A **bound variable** is one that is quantified.
- For instance, if I have the expression $(\forall x)p(x)\land y$, the quantifier $(\forall x)$ quantifies $x$. Since $y$ is not quantified, then $y$ is a free variable.
- However, if I had the expression $(\forall y)((\forall x)p(x)\land y)$, then $y$ is no longer free as it is quantified by the $(\forall y)$ quantifier. Thus it is a bound variable.
    - Note: You are almost never going to see an expression like this in FOL. $y$ will usually belong to a predicate.

# Updated Definition of a Proof
Along with these, there is a refined definition of proofs:

A ***derivation*** or ***proof*** of a FOL-wff $\alpha$ from a set of FOL-wffs $\Gamma$ is a sequence of FOL-wffs, $\alpha_1,\alpha_2,\dots,\alpha_n$ such that:
1. $\alpha_n=\alpha$, and
2. For each $i,1\leq i\leq n$,
    1. $\alpha_i$ is a FOL-wff from $\Gamma$, or
    2. $\alpha_i$ is of the form $(\omega\lor\sim\omega)$ called *axiom*, where $\omega$ is a FOL-wff, or
    3. $\alpha_i$ is a direct consequence of some of the preceding FOL-wffs by virtue of one of the inference rules or by substitution, and
3. Each application of **EI** introduces a *new* constant which does not appear in $\alpha$, and
4. No application of **Gen** using $x$ is made to $\alpha(x)$, if the variable $x$ appears as a free variable in a hypothesis upon which $\alpha(x)$ is deduced, and
5. No application of **Gen** is made using a variable that is free in some $(\exists x)\beta(x)$ to which **EI** has been previously applied.

The first two lines are the same as in chapter 1. However, lines 3, 4 and 5 are new. Notice these rules describe only **EI** and **Gen**. Here is what they all mean:

## 3. Each application of **EI** introduces a *new* constant which does not appear in $\alpha$
When using EI, you **have to** introduce a brand new constant. You can't reuse a constant that already exists, because you're assuming the same entity that satisfies some other expression also satisfies the current expression.

However, for UI, you can **optionally** introduce a new constant. That's why you should use EI before UI.

{{< notice example >}}
The following proof is invalid:

1\. $(\exists x)Even(x)\quad$ from $\Gamma$\
2\. $(\exists x)Odd(x)\quad$ from $\Gamma$\
3\. $Even(a)\quad$ 1, EI, $a$ is a new constant\
4\. $Odd(a)\quad$ 2, EI, $a$ is a constant\
5\. $Odd(a)\land Even(a)\quad$ 4, 3, I6\
6\. $(\exists x)(Odd(x)\land Even(x))\quad$ 5, EQ

Assume $Odd(x)$ defines a predicate for "$x$ is odd" and $Even(x)$ defines "$x$ is even". By reusing the same constant, we are assuming the same constant satisfies both predicates, which is obviously nonsensical (how can a number be both odd and even?).
{{< /notice >}}

## 4. No application of **Gen** using $x$ is made to $\alpha(x)$, if the variable $x$ appears as a free variable in a hypothesis upon which $\alpha(x)$ is deduced
If I start with $C(x)$ and then later say $(\forall x)C(x)$. then I'm basically saying I started with some expression such as $C(m)$ (i.e. Max likes chocolate) and am now concluding that every possible value for $x$ satisfies $C(x)$. I'm essentially saying "Max likes chocolate. Therefore, everybody likes chocolate." This is nonsensical.

Effectively, if you start with a predicate that is not quantified, then you cannot perform **Gen** on it.

## 5 No application of **Gen** is made using a variable that is free in some $(\exists x)\beta(x)$ to which **EI** has been previously applied
If you used **EI** for some expression, you can't use Gen later. If you start with $(\exists x)C(x)$ ("There exists someone who likes chocolate"), then use **EI** to get $C(m)$ ("Max likes choocolate"), you can't later use **Gen** to get $(\forall x)C(x)$ ("Everyone likes chocolate"). That is nonsensical.