+++ 
date = 2023-09-25T18:31:48-04:00
title = "COMP-2310 Proof Guide"
description = ""
slug = ""
authors = []
tags = ['comp-2310']
categories = []
externalLink = ""
series = []
+++

# What is a Proof?
In order to succeed in COMP2310, you need to have a good understanding of proofs. Here's the definition of a proof from the courseware:

> A ***derivation*** or ***proof*** of a wff $\alpha$ from a set of wffs $\Gamma$ in propositional logic is a sequence of wffs, $\alpha_1,\alpha_2,\dots,\alpha_n$ such that $\alpha_n=\alpha$, and for each $i,\;1\leq i\leq n$,
> 1. $\alpha_i$ is a wff in $\Gamma$, or
> 2. $\alpha_i$ is of the form $\omega\lor\lnot\omega$, called *axiom*, where $\omega$ is a wff, or
> 3. $\alpha_i$ is a direct consequence of some of the preceding wffs by substitution or by virtue of one of the inference rules.

This definition perfectly describes a proof. What it translates to is this:
- A proof involves deriving some wff $\alpha$ from a set of wffs called $\Gamma$. Effectively, $\Gamma$ can be understood as your list of premises that you already know, while $\alpha$ is whatever you are trying to prove.
- The "sequence of wffs, $\alpha_1,\alpha_2,\dots,\alpha_n$ such that $\alpha_n=\alpha$" simply means a proof contains many lines such that the last line is what you are trying to prove, which is $\alpha$.
- Each line of the proof must meet one of the three conditions:
  1. It must be one of the premises you start with (it's a wff in $\Gamma$).
  2. It must be the *axiom*, which is $\omega\lor\lnot\omega$ where $\omega$ is any wff. For example: $(\alpha\land\lnot\beta)\lor\lnot(\alpha\land\lnot\beta)$ is a valid line.
  3. It must be the result of applying an equivalence or inference rule on a previous line.

# Tips when Writing Proofs
When writing proofs, follow these general tips:
1. Write your proof method at the top of the proof, before proceeding, in parentheses.
    - If you are simply doing a proof by definition, without using a method, then no proof method is needed.
1. Always state your justification for each line.
    - If you applied an equivalence or inference rule, state the line you applied it to. If you applied E10 on line 3, write *"3, E10"*.
    - If you are stating the premise in a direct proof or proof by contraposition, write *"Premise"*.
    - If you are stating the hypothesis in a proof by contradiction, write *"Hypothesis"*.
    - If you are writing a given premise from $\Gamma$, write *"from $\Gamma$"*.
    - If you are writing the axiom $\omega\lor\lnot\omega$, write *"axiom"*.
2. Don't apply two equivalences/inference rules on the same line. Do one equivalence or inference rule at a time. Otherwise, you are skipping steps and marks will be deducted.
3. Don't apply the same equivalence twice on the same line. Do one at a time.
    - If you have $(p\lor q)\land(r\lor s)$, you may be tempted to write "$(q\lor p)\land(s\lor r)$ 1, E10" as the next line.
    However, E10 was applied twice here. Instead, apply E10 once per line, or marks will be deducted.

# Proof Methods
There are many proof methods to discuss.

## Direct Proof
The exact form in the courseware is:
> To prove that $\vdash(\alpha\Rightarrow\beta)$, we may prove that $\alpha\vdash\beta$. i.e. we may derive a proof of $\beta$ from $\alpha$.

This effectively means, if the wff we are trying to prove is of the form $\alpha\Rightarrow\beta$, then we can assume $\alpha$ (call it the *premise*) and prove $\beta$.

{{< notice example >}}
Prove the following: $\vdash((p\Rightarrow r)\land(r\Rightarrow q))\Rightarrow(p\Rightarrow q)$.

This is of the form $\alpha\Rightarrow\beta$, where $\alpha$ is $(p\Rightarrow r)\land(r\Rightarrow q)$ and $\beta$ is $p\Rightarrow q$. Here is a solution:

(Direct proof)\
1\. $(p\Rightarrow r)\land(r\Rightarrow q)\quad$ Premise\
2\. $p\Rightarrow r\quad$ 1, I2\
3\. $(r\Rightarrow q)\land(p\Rightarrow r)\quad$ 1, E9\
4\. $r\Rightarrow q\quad$ 3, I2\
5\. $p\Rightarrow q\quad$ 2, 4, I5

Thus $((p\Rightarrow r)\land(r\Rightarrow q))\Rightarrow(p\Rightarrow q)\qquad\blacksquare$
{{< /notice >}}