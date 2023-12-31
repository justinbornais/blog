+++ 
date = 2023-09-25T18:31:48-04:00
title = "COMP-2310 Proof Guide"
description = ""
slug = ""
authors = ['Justin Bornais']
tags = ['comp-2310']
categories = []
externalLink = ""
series = []
+++

# What is a Proof?
In order to succeed in COMP2310, you need to have a good understanding of proofs. Here's the definition of a proof from the courseware:

> A ***derivation*** or ***proof*** of a wff $\alpha$ from a set of wffs $\Gamma$ in propositional logic is a sequence of wffs, $\alpha_1,\alpha_2,\dots,\alpha_n$ such that $\alpha_n=\alpha$, and for each $i,\;1\leq i\leq n$,
> 1. $\alpha_i$ is a wff in $\Gamma$, or
> 2. $\alpha_i$ is of the form $\omega\lor\sim\omega$, called *axiom*, where $\omega$ is a wff, or
> 3. $\alpha_i$ is a direct consequence of some of the preceding wffs by substitution or by virtue of one of the inference rules.

This definition perfectly describes a proof. What it translates to is this:
- A proof involves deriving some wff $\alpha$ from a set of wffs called $\Gamma$. Effectively, $\Gamma$ can be understood as your list of premises that you already know, while $\alpha$ is whatever you are trying to prove.
- The "sequence of wffs, $\alpha_1,\alpha_2,\dots,\alpha_n$ such that $\alpha_n=\alpha$" simply means a proof contains many lines such that the last line is what you are trying to prove, which is $\alpha$.
- Each line of the proof must meet one of the three conditions:
  1. It must be one of the premises you start with (it's a wff in $\Gamma$).
  2. It must be the *axiom*, which is $\omega\lor\sim\omega$ where $\omega$ is any wff. For example: $(\alpha\land\sim\beta)\lor\sim(\alpha\land\sim\beta)$ is a valid line.
  3. It must be the result of applying an equivalence or inference rule on a previous line.

# Tips when Writing Proofs
When writing proofs, follow these general tips:
1. Write your proof method at the top of the proof, before proceeding, in parentheses.
    - If you are simply doing a proof by definition, without using a method, then no proof method is needed.
1. Always state your justification for each line.
    - If you applied an equivalence or inference rule, state the line you applied it to. If you applied E10 on line 3, write *"3, E10"*.
    - If you are stating the premise in a direct proof or proof by contraposition, write *"Premise"*.
    - If you are stating the hypothesis in a proof by contradiction or vacuous proof, write *"Hypothesis"*.
    - If you are stating the assumption in an indirect proof, write *"Assumption"*.
    - If you are writing a given premise from $\Gamma$, write *"from $\Gamma$"*.
    - If you are writing the axiom $\omega\lor\sim\omega$, write *"axiom"*.
2. Don't apply two equivalences/inference rules on the same line. Do one equivalence or inference rule at a time. Otherwise, you are skipping steps and marks will be deducted.
3. Don't apply the same equivalence twice on the same line. Do one at a time.
    - If you have $(p\lor q)\land(r\lor s)$, you may be tempted to write "$(q\lor p)\land(s\lor r)$ 1, E10" as the next line.
    However, E10 was applied twice here. Instead, apply E10 once per line, or marks will be deducted.

# Proof Methods
There are many proof methods to discuss.

## Direct Proof
This is one of the most common proofs. The exact form in the courseware is:
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

## Proof by Contradiction
This is probably the second most common proof. The exact form in the courseware is:
> To prove that $\vdash\omega$, we may proceed to prove that $\sim\omega\vdash false$.

This means, if we're trying to prove something (i.e. $\omega$), we can assume the negation ($\sim\omega$) and show that we eventually lead to false.

{{< notice example >}}
Prove the following: $\vdash((p\Rightarrow r)\land(r\Rightarrow q))\Rightarrow(p\Rightarrow q)$.

(Proof by Contradiction)\
1\. $((p\Rightarrow r)\land(r\Rightarrow q))\land\sim(p\Rightarrow q)\quad$ Hypothesis\
2\. $(p\Rightarrow r)\land(r\Rightarrow q)\quad$ 1, I2\
3\. $p\Rightarrow r\quad$ 2, I2\
4\. $(r\Rightarrow q)\land(p\Rightarrow r)\quad$ 2, E9\
5\. $r\Rightarrow q\quad$ 4, I2\
6\. $p\Rightarrow q\quad$ 3, 5, I5\
7\. $\sim(p\Rightarrow q)\land((p\Rightarrow r)\land(r\Rightarrow q))\quad$ 1, E9\
8\. $\sim(p\Rightarrow q)\quad$ 7, I2\
9\. $(p\Rightarrow q)\land\sim(p\Rightarrow q)\quad$ 6, 8, I6\
10\. $false\quad$ 9, E1

Thus $((p\Rightarrow r)\land(r\Rightarrow q))\Rightarrow(p\Rightarrow q)\qquad\blacksquare$
{{< /notice >}}

## Indirect Proof
This proof is used sparingly, but is also beneficial to know. The exact form in the courseware is:
> To prove that $\vdash(\alpha\Rightarrow\beta)$, we may proceed to prove that $\vdash(\sim\beta\Rightarrow\sim\alpha)$.

This is effectively the opposite of a direct proof. We prove its *contrapositive* instead. Then, you proceed with the proof using another proof method.

{{< notice example >}}
Prove the following: $\vdash(\sim p\Rightarrow p)\Rightarrow p$

(Indirect proof) We shall prove that $\vdash\sim p\Rightarrow\sim(\sim p\Rightarrow p)$

(Direct proof)\
1\. $\sim p\quad$ Assumption\
2\. $\sim(p\lor p)\quad$ 1, E4\
3\. $\sim(\sim p\lor p)\quad$ 2, E15\
4\. $\sim(\sim p\Rightarrow p)\quad$ 4, E18

Thus $\vdash\sim p\Rightarrow\sim(\sim p\Rightarrow p)$.

Consequently, $\vdash(\sim p\Rightarrow p)\Rightarrow p\qquad\blacksquare$

See how there's two conclusion statements? That's because we have to show we finished the direct proof, then we have to finish the indirect proof.
{{< /notice >}}

## Proof by Cases
This is useful in later chapters, primarily chapters 4-7. The exact form in the courseware is:
> To prove that $\vdash(\alpha_1\lor\alpha_2\lor\dots\lor\alpha_k)\Rightarrow\beta$, we may proceed to prove that $\vdash\alpha_1\Rightarrow\beta$ and $\vdash\alpha_2\Rightarrow\beta$ and $\dots$ and $\vdash\alpha_k\Rightarrow\beta$.

Then with each case, you need to specify a proof method and prove each case.

{{< notice note >}}
The order of cases doesn't matter.
{{< /notice>}}

{{< notice example >}}
Prove the following: $\vdash((\sim p\Rightarrow p)\lor((\sim p\Rightarrow q)\land\sim q))\Rightarrow p$.

(Proof by Cases)

Case 1: Prove that $\vdash(\sim p\Rightarrow p)\Rightarrow p$. (see the Indirect Proof example [above](/posts/comp-2310-info-of-proofs/#indirect-proof))

Case 2: Prove that $\vdash((\sim p\Rightarrow q)\land\sim q)\Rightarrow p$.

(Direct prooof)\
1\. $(\sim p\Rightarrow q)\land\sim q\quad$ Premise\
2\. $\sim p\Rightarrow q\quad$ 1, I2\
3\. $\sim q\land (\sim p\Rightarrow q)\quad$ 1, E9\
4\. $\sim q\quad$ 3, I2\
5\. $\sim p\quad$ 4, 2, I4\
6\. $p\quad$ 5, E15

Hence $\vdash((\sim p\Rightarrow q)\land\sim q)\Rightarrow p$.

Thus, $\vdash((\sim p\Rightarrow p)\lor((\sim p\Rightarrow q)\land\sim q))\Rightarrow p\qquad\blacksquare$
{{< /notice >}}

## Bidirectional Proof
This is used whenever you are trying to prove a wff with a bidirectional. The exact form in the courseware is:
> To prove that $\vdash\alpha\Leftrightarrow\beta$, we may prove that $\vdash\alpha\Rightarrow\beta$ and $\vdash\beta\Rightarrow\alpha$.

Similarly to a proof by cases, break the proof up into two cases and prove each case separately.
{{< notice note >}}
The order in which you prove them doesn't matter.
{{< /notice>}}
{{< notice note >}}
If you only use equivalences for one side of the proof (no inference rules), then this greatly shortens the bidirectional proof as you only need to write "Same as above case but in the reverse order."
{{< /notice>}}

{{< notice example >}}
(Simple example to show the format of the proof)\
Prove that $\vdash(p\lor p)\Leftrightarrow p$.

(Bidirectional proof)

(i) Prove that $\vdash(p\lor p)\Rightarrow p$.

(Direct proof)\
1\. $p\lor p\quad$ Premise\
2\. $p\quad$ 1, E4

Hence $\vdash(p\lor p)\Rightarrow p$.

(ii) Prove that $\vdash p\Rightarrow(p\lor p)$.\
Same as above proof but in the reverse order.\
Hence $\vdash p\Rightarrow(p\lor p)$.

Combining the results of (i) and (ii), we have $\vdash(p\lor p)\Leftrightarrow p\qquad\blacksquare$
{{< /notice >}}

## Trivial Proof
This is hardly used at all, except for specific circumstances. The exact form in the courseware is:
> To prove that $\vdash\alpha\Rightarrow\beta$, we may attempt to prove that $\vdash\beta$.

This means we are only proving $\beta$ with the axiom $\omega\lor\sim\omega$.
{{< notice example >}}
Prove that $\vdash p\Rightarrow\sim(q\land\sim q)$.

(Trivial proof)\
1\. $\sim q\lor\sim q\quad$ axiom\
2\. $\sim(q\land\sim q)\quad$ 1, E16

Thus $\vdash p\Rightarrow\sim(q\land\sim q)\qquad\blacksquare$
{{< /notice >}}

## Vacuous Proof
Honestly, I am not even sure if I have used this proof method before. The exact form in the courseware is:
> To prove that $\vdash\alpha\Rightarrow\beta$, we may attempt to prove that $\vdash\alpha\Rightarrow false$

{{< notice example >}}
Prove that $\vdash(p\land\sim p)\Rightarrow(q\lor\sim p)$

(Vacuous proof)\
1\. $p\land\sim p\quad$ Hypothesis\
2\. $false\quad$ 1, E1

Hence, $\vdash(p\land\sim p)\Rightarrow(q\lor\sim p)\qquad\blacksquare$
{{< /notice >}}

# Summary
These are 8 proof methods (including proof by definition) to help with proofs in 2310. Understanding how these work as well as how to format them will ensure you success in 2310 in the future.