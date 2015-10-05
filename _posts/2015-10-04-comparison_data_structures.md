---
layout: post
title: "Overview of some data structures and comparison between different implementation of them"
date: 2015-10-04
header-img: "img/post-bg-02.png"
---

Data structures are designed to optimze specific operations in applications. From an abstract point of view, operations of data structures could be concluded as insert, remove, query, etc. Different data structures have different time complexity between these operations. We always seek for the best suitable data structure for each problems we faced up. Even for a same computational problem, if our resources are limited from different perspective (time, space, etc.), we might try different data structures.\\
In this blog, some useful data structures are listed, following the catalog of algorithmic problems in *The algorithm design manual* [^skiena1998algorithm], and we discuss the different performance between difference implementation of them.I simply cite the input description and problem description of each data structures in the book.

# Dictionaries
**Input description**: A set of $n$ records, each identified by one or more key fields.

**Problem description**: Build and maintain a data structure to efficiently locate, insert and delete the record associated with any query key $q$. The following table shows the time complexity for each operation of different implementation of dictionaries in average case:

|Implementation|Query|Insert|Delete|Scenior|
|--------------|-----|------|------||
|Unsorted linked lists|$O(n)$|$O(1)$|$O(n)$||
|Unsorted array|$O(n)$|$O(1)$|$O(n)$||
|Sorted linked lists|$O(n)$|$O(n)$|$O(n)$||
|Sorted array|$O(\lg n)$|$O(n)$|$O(n)$||
|Hash tables|$O(1)$|$O(1)$|$O(1)$||
|Binary search trees|$O(\lg n)$|$O(\lg n)$|$O(\lg n)$||
|B-trees|NA|NA|NA|Query secondary storage|
|Skip lists|$O(\lg n)$|$O(\lg n)$|$O(\lg n)$||

# Reference
[^skiena1998algorithm]: Skiena, Steven S. The algorithm design manual: Text. Vol. 1. Springer Science & Business Media, 1998.

