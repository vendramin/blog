---
title: 'Can we use matrices with parameters?'
date: 2025-11-27
author: Andrew Darlington
categories:
  - questions
tags:
  - matrix
  - linear algebra
---
I believe the matrix has to be defined over a polynomial ring. For example, the
code 
```
R<x> := PolynomialRing(Integers());
M := Matrix(R,2,2,[[x,2],[3,x-1]]);
```
produces the matrix 
```
[    x     2]
[    3 x - 1]
```
You can compute with this thing too. For example,
```
Determinant(M);
```
gives `x^2−x−6`. If you then wanted to change the base ring to, say
$\mathbb{Q}[x]$, we proceed as follows: 
```
S<x> := PolynomialRing(Rationals());
N := ChangeRing(M,S);
```

