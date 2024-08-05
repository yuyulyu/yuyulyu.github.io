---
title: Hash Table
# description: Write down description here.
author: yoyo
date: 2024-05-01 15:56:00 +0800
categories: [Data Structure and Algorithm, Data Structure]
tags: [hash table]
---

## Hash Table

![Desktop View](/assets/image/hash-table-1.jpg){: .normal }

### Collisions

There can be different keys \(k_1\), \(k_2\) for which \(h(k_1) = h(k_2)\)

$$
h(k_1) = h(k_2)
$$

### Chaining**

![Desktop View](/assets/image/hash-table-2.jpeg){: .normal }

### Open addressing

Make use of spare space, for example:
  - **Linear probing**: Scan forward through the array.
  - **Quadratic probing**: \(h(k,i) = (h(k) + c_1 i + c_2 i^2) \% M\)
  - **Double hashing**: \(H(k,i) = (h_1(k) + i \cdot h_2(k)) \% M\)



