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