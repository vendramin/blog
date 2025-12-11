---
title: 'The Promislow group'
date: 2025-11-27
author: VUB
categories:
  - questions
tags:
  - group
  - infinite group
  - Promislow group
---
**Exercise.** Let $P=\langle a,b: a^{-1}b^2a=b^{-2}, b^{-1}a^2b=a^{-2}\rangle$ be the 
Promislow group. Prove the following statements:
1. The subgroup $N=\langle a^2,b^2,(ab)^2\rangle$ is 
normal in $P$ and free abelian of rank three. 
2. The group $P/N$ is isomorphic to the Klein group. 

**Partial solution.**
We construct the group $P$, the subgroup $N$ and 
the quotient group $P/N$: 
```
P<a,b> := Group < a,b | a^-1*b^2*a*b^2, b^-1*a^2*b*a^2 >;
x := a^2;
y := b^2;
z := (a*b)^2;
N := sub<P|x,y,z>;
Q, p := quo<P|N>;
```
It is easy to verify that 
$P/N\simeq C_2\times C_2$. In fact, the command 
`GroupName(Q);` returns `C2^2`. 

Some questions: 

* Why `IsAbelian(Q)` doesn’t work? 

The function `IsAbelian` is defined for `GrpLie`, `GrpFin`, `GrpPerm`,
`GrpMat`, `GrpPC` and `GrpGPC` while in this case `Q` is still a `GrpFP`; we
need to change the type!

