---
layout: post
title: "Study notes for TAOCP: Searching Algorithms"
date: 2015-09-26
header-img: "img/post-bg-07.jpg"
---

# Sequential Searching
When doing a sequential search, "BEGIN AT THE BEGINNING, and go on till you find the right key; then stop", as it is defined in the text, it is fairly simple at first glance. But there are different ways implementing the description above. Now let's take a look at them and the performance of them.

First, let's look at the first sequential search algorithm, **Algorithm S** discussed in this chapter:

**Algorithm S** (*Sequential search*). Given a table of records $R_1, R_2, ..., R_N,$ whose respective keys are $K_1,K_2,...,K_N$, this algorithm searches for a given argument $K$. We assume that $N\geq1$. \\
**S1**. \[Initialize.\] Set $i\leftarrow1$. \\
**S2**. \[Compare.\] If $K=K_i$, the algorithm terminates succesfully. \\
**S3**. \[Advance.\] Increase $i$ with $1$. \\
**S4**. \[End of file?\] If $i\leq N$, go back to S2. Otherwise the algorithm terminates unsuccesfully.

The most time consumming operations of this algorithm are the two comparison operations in **S2** and **S4**, which give a $O(2n)$ complexity. This chapter gives a smart method. With a straightforward change, this algorithm could be faster unless the list of record is very short. Let's take a look at the **Algorithm Q** described in the textbook.

**Algorithm Q** (*Quick sequential search*). This algorithm is the same as Algorithm S, except that it assumes the presence of a dummy record $R\_{N+1}$ at the end of the file. \\
**Q1**. \[Initialize.\] Set $i\leftarrow1$, and set $K\_{N+1}\leftarrow K$. \\
**Q2**. \[Compare.\] If $K=K_i$, go to Q4. \\
**Q3**. \[Advance.\] Increase $i$ by $1$ and return to Q2. \\
**Q4**. \[End of file?\] If $i\leq N$, the algorithm terminates successfully; otherwise it terminates unsuccessfully ($i=N+1$).

In this algorithm, the comparison in Q4 only be evaluated once, at the end of this file. So the comparisons give a $O(n)$ complexity in this algorithm.
