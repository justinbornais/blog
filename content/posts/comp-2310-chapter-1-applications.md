+++ 
date = 2023-09-29T18:31:48-04:00
title = "COMP-2310 Chaper 1 - Applications"
description = ""
slug = ""
authors = ['Justin Bornais']
tags = ['comp-2310']
categories = []
externalLink = ""
series = []
+++

Section 1.8 of chapter 1 of the COMP2310 courseware discusses a concept called **Applications**. This describes using what was learned about formal proofs in propositional logic to test the validity of certain real-world arguments.

In this blog, I will go over some examples to see how we can use propositional logic to prove if certain arguments make sense. Each proof follows a given structure:
1. Denote each proposition with a variable (usually upper-case but doesn't have to be), such as $A$, $B$, $C$, $\dots$
2. Translate each statement into a wff.
3. Prove the conclusion with the given premises.

Some general tips when solving:
1. Try to only denote the positive expressions as variables (i.e. if the statement reads "John does not walk", denote *J* as "John walks" and convert the expression to $\lnot J$).
2. Once the statements are properly translated into wffs, do your best to try and understand conceptually why the logic works out.

# Example 1
There is a poker game going on. If Nick wins, then Matt will throw a party. If Spencer wins, then Tom will throw a party. It is the case that either Nick or Spencer will win.
If Hunter wins, then Tom will not throw a party, and if Spencer wins, then Matt will not throw a party. Therefore, Matt will throw a party if and only if Tom does not throw a party.

## Solution
Let N denote "Nick wins",\
$\quad$ S denote "Spencer wins",\
$\quad$ H denote "Hunter wins",\
$\quad$ M denote "Matt will throw a party",\
$\quad$ T denote "Tom will throw a party".

The sentence "There is a poker game going on" does not need to be translated at all, as there is nothing useful about it.\
The sentence "If Nick wins, then Matt will throw a party" can be translated to $N\Rightarrow M$\
The sentence "If Spencer wins, then Tom will throw a party" can be translated to $S\Rightarrow T$\
The sentence "It is the case that either Nick or Spencer will win" can be translated to $(N\lor S)\land\lnot(N\land S)$\
The sentence "If Hunter wins, then Tom will not throw a party" can be translated to $H\Rightarrow\lnot T$\
The statement "If Spencer wins, then Matt will not throw a party" can be translated to $S\Rightarrow\lnot M$.