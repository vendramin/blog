---
title: 'Random elements in group algebras'
date: 2025-11-27
author: VUB
categories:
  - questions
tags:
  - random element
  - group algebra
  - algebra
--- 
Is it possible to get a random element of $\mathbb{C}[G]$? If not, what is the problem?

Magma doesn’t appear to like giving random elements of an infinite set (it even
complains when you ask for a random integer, for example, without giving it any
bounds). Instead of using `ComplexField`, we will use the field
$\mathbb{Q}(i)$. Here is a concrete way to generate some sort of random
elements group algebras: 
```
> G := Sym(3);
> Q<i> := QuadraticField(-1);
> A := GroupAlgebra(Q,G);
> x := Random(-100,100);
> y := Random(-100,100);
> z := x+i*y;
41*i + 34
```
Now 
```
> A!z*Random(G);
(41*i + 34)*(1, 2, 3)
```
There should be a better way to get 
_better_ random elements of $\mathbb{C}[G]$. No? 

