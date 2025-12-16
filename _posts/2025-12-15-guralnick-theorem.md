---
title: 'Guralnick theorem'
date: 2025-12-15
author: Leandro Vendramin
categories:
  - exercises
tags:
  - group
  - commutator
---
**Exercise.** Prove the following result:

**Theorem (Guralnick).**
There is a group $G$ of order $\leq200$ such that $[G,G]\ne\lbrace [x,y]:x,y\in G\rbrace$
if and only if $n\in\lbrace 96,128,144, 162, 168, 192\rbrace$. 

The theorem appeared in [Guralnick, R. Commutators and commutator subgroups.
_Adv. in Math._ 45 (1982), no. 3, 319–330].    

**Solution.** To simplify a bit the presentation, we
first define a function that returns the set 
of commutators of a group:
```
> SetOfCommutators := function(G)
function> return { (x,y) : x,y in G };
function> end function;
```
Now we use this function. We send the parameter `Warning := false` to the
function `SmallGroups` to avoid the warning messages.  Otherwise, Magma warns
us that the requested calculation involves a huge number of groups:
```
> time { #G : G in SmallGroups([1..200]:Warning:=false) | 
> not #DerivedSubgroup(G) eq #SetOfCommutators(G) };
{ 96, 128, 144, 162, 168, 192 }
Time: 34.360
```
The calculation took 34 seconds. 

