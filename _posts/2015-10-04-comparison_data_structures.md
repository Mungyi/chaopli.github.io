---
layout: post
title: "Overview of two data structures: Dictionary and Priority queue"
date: 2015-10-04
header-img: "img/post-bg-02.png"
---

Data structures are designed to optimze specific operations in applications. From an abstract point of view, operations of data structures could be concluded as insert, remove, query, etc. Different data structures have different time complexity between these operations. We always seek for the best suitable data structure for each problems we faced up. Even for a same computational problem, if our resources are limited from different perspective (time, space, etc.), we might try different data structures.\\
In this blog, some useful data structures are listed, following the catalog of algorithmic problems in *The algorithm design manual* [^skiena1998algorithm], and we discuss the different performance between difference implementation of them.I simply cite the input description and problem description of each data structures in the book.

# Dictionaries
**Input description**: A set of $n$ records, each identified by one or more key fields.

**Problem description**: Build and maintain a data structure to efficiently locate, insert and delete the record associated with any query key $q$. \\
The following table shows the time complexity for each operation of different implementation of dictionaries in average case:

|Implementation|Query|Insert|Delete|Scenario|
|--------------|-----|------|------|--------|
|Unsorted array|$O(n)$|$O(1)$|$O(n)$||
|Sorted array|$O(\lg n)$|$O(n)$|$O(n)$|few insertion operations|
|Hash tables|$O(1)$|$O(1)$|$O(1)$||
|Binary search trees|$O(\lg n)$|$O(\lg n)$|$O(\lg n)$||
|B-trees|NA|NA|NA|Query secondary storage|
|Skip lists|$O(\lg n)$|$O(\lg n)$|$O(\lg n)$||

# Priority Queues
**Input description**: A set of records with numerically or otherwise totally-ordered keys.

**Problem description**: Build and maintain a data structure for providing quick access to the *smallest* or *largest* key in the set.


|Implementation|Query|Insert|Delete|Scenario|
|--------------|-----|------|------|--------|
|Sorted array|$O(1)$|$O(n)$|$O(n)$|few insertion operations|
|Binary heaps|$O(\lg n)$|$O(\lg n)$|$O(\lg n)$|data size is known|
|Bounded height priority queue|$O(1)$|$O(1)$|$O(1)$|key range is known|
|Binary search trees|$O(\lg n)$|$O(\lg n)$|$O(\lg n)$|general case|
|[Fibonacci and pairing heaps (click)](https://www.cise.ufl.edu/~sahni/dsaaj/enrich/c13/pairing.htm)||||speed up *decrease-key* operation|

# Reference
[^skiena1998algorithm]: Skiena, Steven S. The algorithm design manual: Text. Vol. 1. Springer Science & Business Media, 1998.
