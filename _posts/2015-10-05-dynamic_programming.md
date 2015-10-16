---
layout: post
title: "Dynamic programming overview: from mathematical optimization to computer programming"
date: 2015-10-05
header-img: "img/post-bg-dp.JPG"
---

[Wikipedia](https://en.wikipedia.org/wiki/Dynamic_programming#cite_note-1) gives the following description of dynamic programming (DP): In mathematics, computer science, economics, and bioinformatics, *dynamic programming* is a method for solving a complex problem by breaking it down into a collection of simpler subproblems. It is applicable to problems exhibiting the properties of *overlapping subproblems* [^dasguptaalgorithms] and *optimal substructure*. A problem that can be solved optimally by breaking it into sub-problems and then recursively finding the optimal solutions to the sub-problems is said to have optimal substructure. When applicable, DP takes far less time than other methods that don't take advantage of the subproblem overlap (like depth-first search).

# Principles of Dynamic Programming (Mathematical Perspective)
Let $d\_i\in\Delta$ be a desicion, where $\Delta$ be the set of eligible decisions, and $H$ be the *objective function*. Then the optimal solution of the optimization problem opt$\_\{d\in\Delta\}{H(d)}$ would be $H^\*=H(d^\*)$, where $d^\*$ means an optimal sequence of the decisions.

# Reference
[^dasguptaalgorithms]: S. Dasgupta, C.H. Papadimitriou, and U.V. Vazirani, 'Algorithms', p 173, available [*here*](http://www.cs.berkeley.edu/~vazirani/algorithms.html)
