---
layout: post
title: "Study notes for TAOCP: Sequential search and Fibonaccian search"
date: 2015-09-26
header-img: "img/post-bg-07.jpg"
---

# Sequential Searching
When doing a sequential search, "BEGIN AT THE BEGINNING, and go on till you find the right key; then stop", as it is defined in the text, it is fairly simple at first glance. But there are different ways implementing the description above. Now let's take a look at them and the performance of them.

First, let's look at the first sequential search algorithm, **Algorithm S** discussed in this chapter:

**Algorithm S** (*Sequential search*). Given a table of records $R\_1, R\_2, ..., R\_N,$ whose respective keys are $K\_1,K\_2,...,K\_N$, this algorithm searches for a given argument $K$. We assume that $N\geq1$. \\
**S1**. \[Initialize.\] Set $i\leftarrow1$. \\
**S2**. \[Compare.\] If $K=K\_i$, the algorithm terminates succesfully. \\
**S3**. \[Advance.\] Increase $i$ with $1$. \\
**S4**. \[End of file?\] If $i\leq N$, go back to S2. Otherwise the algorithm terminates unsuccesfully.

The most time consumming operations of this algorithm are the two comparison operations in **S2** and **S4**, which give a $O(2n)$ complexity. This chapter gives a smart method. With a straightforward change, this algorithm could be faster unless the list of record is very short. Let's take a look at the **Algorithm Q** described in the textbook.

**Algorithm Q** (*Quick sequential search*). This algorithm is the same as Algorithm S, except that it assumes the presence of a dummy record $R\_{N+1}$ at the end of the file. \\
**Q1**. \[Initialize.\] Set $i\leftarrow1$, and set $K\_{N+1}\leftarrow K$. \\
**Q2**. \[Compare.\] If $K=K_i$, go to Q4. \\
**Q3**. \[Advance.\] Increase $i$ by $1$ and return to Q2. \\
**Q4**. \[End of file?\] If $i\leq N$, the algorithm terminates successfully; otherwise it terminates unsuccessfully ($i=N+1$).

In this algorithm, the comparison in Q4 only be evaluated once, at the end of this file. So the comparisons give a $O(n)$ complexity in this algorithm.

# Fibonaccian search
Fibonaccian numbers can analogous the power of 2, hence a similar phenomenon occurs in searching. We can use fibonaccian numbers analogous binary search. This procedure here about to discuss should be distinguished with another numerical procedure called "Fibonacci search", which is used to locate the maximum of a unimodal function [^avriel1966optimality]. \\
![fibo_tree](../../../../img/{{ page.date | date: '%Y-%m-%d'}}/fibonacci_tree.svg)
The above figure shows a Fibonacci tree of order 6. In general, the Fibonacci tree of order k has $F\_{k+1}-1$ internal nodes and $F\_{k+1}$ external nodes, and it is constructed as follows: 

*  If $k=0$ or $k=1$, the tree is simply an external node $0$. 
*  If $k\geq2$, the root is $F\_k$; the left subtree is the Fibonacci tree of order $k-1$; and the right subtree is the Fibonacci tree of order $k-2$ with all numbers increased by $F\_k$.

Once we have an eye on the Fibonacci tree, we can use the following algorithm to do a Fibonaccian search:

**Algorithm F** (*Fibonaccian search*). Given a table of records $R\_1, R\_2, ..., R\_N$ whose keys are in increasing order $K\_1<K\_2<\cdots<K\_N$, this algorithm searches for a given argument $K$. \\
For convenience in description, we assume that $N+1$ is a perfect Fibonacci number, $F\_{k+1}$. It is not difficult to make the method work for arbitrary $N$, if a suitable initialisation is provided. \\
**F1.** \[Initialize.\] Set $i\leftarrow F\_k$, $p\leftarrow F\_{k-1}$, $q\leftarrow F\_{k-2}$. \\
**F2.** \[Compare.\] If $K<K\_i$, go to step F3; if $K>K\_i$, go to F4; and if $K=K\_i$, the algorithm terminates successfully. \\
**F3** [Decrease $i$.] If $q=0$, the algorithm terminates unsuccesfully. Otherwise set $i\leftarrow i-q$, $p\leftarrow p-q$, and set $(p,q)\leftarrow(q,p-q)$; then return to F2. \\
**F4** [Increase $i$.] If $p=1$, the algorithm terminates unsuccessfully. Otherwise set $i\leftarrow i+q$, $p\leftarrow p-q$, then $q\leftarrow q-p$, and return to F2.

# Reference
[^avriel1966optimality]: Avriel, Mordecai, and Douglass J. Wilde. "Optimality proof for the symmetric Fibonacci search technique." Fibonacci Quarterly 4.3 (1966): 265-269.
