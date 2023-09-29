+++ 
date = 2023-09-29T17:14:49-04:00
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
1. Denote each proposition with a variable (usually upper-case but doesn't have to be), such as $A$, $B$, $C$, etc.
2. Translate each statement into a wff.
3. Prove the conclusion with the given premises.

Some general tips when solving:
1. Try to only denote the positive expressions as variables (i.e. if the statement reads "John does not walk", denote *J* as "John walks" and convert the expression to $\lnot J$).
2. Once the statements are properly translated into wffs, do your best to try and understand conceptually why the logic works out.

# Example 1
There is a poker game going on. If Nick wins, then Matt will throw a party. If Spencer wins, then Tom will throw a party. It is the case that either Nick or Spencer will win.
If Nick wins, then Tom will not throw a party, and if Spencer wins, then Matt will not throw a party. Therefore, Matt will throw a party if and only if Tom does not throw a party.

## Solution
Let N denote "Nick wins",\
$\quad$ S denote "Spencer wins",\
$\quad$ M denote "Matt will throw a party",\
$\quad$ T denote "Tom will throw a party".

The sentence "There is a poker game going on" does not need to be translated at all, as there is nothing useful about it.\
The sentence "If Nick wins, then Matt will throw a party" can be translated to $N\Rightarrow M$\
The sentence "If Spencer wins, then Tom will throw a party" can be translated to $S\Rightarrow T$\
The sentence "It is the case that either Nick or Spencer will win" can be translated to $(N\lor S)\land\lnot(N\land S)$\
The sentence "If Nick wins, then Tom will not throw a party, and if Spencer wins, then matt will not throw a party " can be translated to $(N\Rightarrow\lnot T)\land (S\Rightarrow\lnot M)$\
The conclusion "Matt will throw a party if and only if Tom does not throw a party" can be translated to $M\Leftrightarrow\lnot T$.

{{< notice note >}}
The third statement could've been translated to $(N\lor S)$. However, the purpose of the statement was to say *only **one** of them* will win. The final wff $(N\lor S)\land\lnot(N\land S)$ translates to
"Nick or Spencer will win, and both of them won't win" which has the same meaning.

The conclusion is a bidirectional because it said "if and only if".
{{< /notice >}}

We thus have:\
$\qquad P_1:\quad N\Rightarrow M$\
$\qquad P_2:\quad S\Rightarrow T$\
$\qquad P_3:\quad (N\lor S)\land\lnot(N\land S)$\
$\qquad P_4:\quad (N\Rightarrow\lnot T)\land (S\Rightarrow\lnot M)$\
$\qquad C:\quad M\Leftrightarrow\lnot T$

and we are to prove that $P_1,P_2,P_3,P_4\vdash C$.

1\. $N\Rightarrow M\quad$ from $\Gamma$\
2\. $S\Rightarrow T\quad$ from $\Gamma$\
3\. $(N\lor S)\land\lnot(N\land S)\quad$ from $\Gamma$\
4\. $(N\Rightarrow\lnot T)\land(S\Rightarrow\lnot M)\quad$ from $\Gamma$\
5\. $(S\Rightarrow\lnot M)\land(N\Rightarrow\lnot T)\quad$ 4, E9\
6\. $(S\Rightarrow\lnot M)\quad$ 5, I2\
7\. $(\lnot\lnot M\Rightarrow\lnot S)\quad$ 6, E19\
8\. $(M\Rightarrow\lnot S)\quad$ 7, E15\
9\. $N\lor S\quad$ 3, I2\
10\. $S\lor N\quad$ 9, E10\
11\. $\lnot\lnot S\lor N\quad$ 10, E15\
12\. $\lnot S\Rightarrow N\quad$ 11, E18\
13\. $M\Rightarrow N\quad$ 8, 12, I5\
14\. $N\Rightarrow\lnot T\quad$ 4, I2\
15\. $M\Rightarrow\lnot T\quad$ 13, 14, I5\
16\. $\lnot T\Rightarrow\lnot S\quad$ 2, E19\
17\. $\lnot T\Rightarrow N\quad$ 16, 12, I5\
18\. $\lnot T\Rightarrow M\quad$ 17, 1, I5\
19\. $(M\Rightarrow\lnot T)\land(\lnot T\Rightarrow M)\quad$ 15, 18, I6\
20\. $M\Leftrightarrow\lnot T\quad$ 19, E20

Hence, $P_1,P_2,P_3,P_4\vdash C\qquad\blacksquare$