---
title: 'Computing preimages'
date: 2025-12-05
author: Leandro Vendramin
categories:
  - questions
tags:
  - homomorphism
  - group
  - quotient
  - normal subgroup
---
Let $G=SL_2(5)$ and $p\colon G\to G/Z(G)$ be the canonical 
map. Typically, Magma will represent $G/Z(G)$
as a permutation group:
```
> G := SL(2,5);
> Z := Center(G);
> Q, p := quo< G|Z >;
> GroupName(Q);
A5
```
Let us compute some preimages. Let us take a random element 
`y` of `Q`, namely 
```
> y := Random(Q);
> y;
(1, 3, 5, 4, 2)
> x := y @@ p;
> x;
[1 0]
[4 1]
```
How do I get _all_ the preimages of an element $y$? One needs the (right)
coset $(\ker p)x$, where $x$ is such that $p(x)=y$. For this, I need to convert
my matrix group into a permutation group: 
```
> f, P := PermutationRepresentation(G);
```
The map `f` we get is a bijective group homomorphism $SL_2(5)\to P$, where $P$ is
a permutation group. The preimage of $y$ has size two, and it is 
the right coset $(\ker p)x$. Let us compute this: 
```
> N := f(K);
> K := Kernel(p);
```
Now the preimage is the set 
```
> { Inverse(f)(n*f(x)) : n in N };
{
    [1 0]
    [4 1],

    [4 0]
    [1 4]
}
```
