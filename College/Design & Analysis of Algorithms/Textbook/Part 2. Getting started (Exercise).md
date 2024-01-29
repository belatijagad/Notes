## 2.1 Insertion sort

**Problem 1**. Using Figure 2.2 as a model, illustrate the operation of `Insertion-Sort` on an array initially containing the sequence $\langle31,41,59,26,41,58\rangle$.

**Problem 2**. Consider the procedure `Sum-Array` on the facing page. It computes the sum of the $n$ number in array $A[1:n]$. State a loop invariant for this procedure, and use its initialization, maintenance, and termination properties to show that the `Sum-Array` procedure returns the sum of the numbers in $A[1:n]$.

```py
sum=0
for i=1 to n
	sum = sum + A[i]
return sum
```

**Problem 3**. Rewrite the `Insertion-Sort` procedure to sort into monotonically decreasing instead of monotonically increasing order.

**Problem 4**. Consider the searching problem:

**Input**: A sequence of $n$ numbers $\langle a_1,a_2,\dots,a_n\rangle$ stored in array $A[1:n]$ and a value $x$.

**Output**: An index $i$ such that $x$ equals $A[i]$ or the special value `NIL` if $x$ does not appear in $A$.

Write pseudo code for *linear search*, which scans through the array from beginning to end, looking for $x$. Using loop invariant, prove that your algorithm is correct. Make sure that your loop invariant fulfills the three necessary properties.

**Problem 5**. Consider the problem of adding two $n$-bit binary integers $a$ and $b$, stored in two $n$-element arrays $A[0:n-1]$ and $B[0:n-1]$, where each element is either 0 or 1, $a=\sum^{n-1}_{i=0}{A[i]\cdot2^i}$, and $b=\sum^{n-1}_{i=0}{B[i]\cdot2^i}$. The sum $c=a+b$ of the two integers should be stored in binary form in an $(n+1)$-element array $C[0:n]$, where $c=\sum^{n}_{i=0}{C[i]\cdot2^i}$. Write a procedure `Add-Binary-Integers` that takes as input arrays $A$ and $B$, along with the length $n$, and returns array $C$ holding the sum.

## 2.2 Analyzing algorithms

## 2.3 Designing algorithms
