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

**Problem 1**.  Express the function $n^3/1000+100n^2-100n+3$ in terms of $\Theta$ notation.

**Problem 2**. Consider sorting $n$ numbers stored in array $A[1:n]$ by first finding the smallest element of $A[1:n]$ and exchanging it with the element in $A[1]$. Then find the smallest element of $A[2:n]$, and exchange it with $A[2]$. Continue this manner for the first $n-1$ elements of $A$. Write the pseudo code for this algorithm, which is known as *selection sort*. What loop invariant does this algorithm maintain? Why does it need to run for only $n-1$ elements, rather than for all $n$ elements? Give the worst-case running time of selection in $\Theta$-notation. Is the best case running time any better?

**Problem 3**. Consider linear search again *(see exercise 2.1-4)*. How many elements of the input array need to be checked on the average, assuming that the element being created for is equally likely to be any element in the array? How about the worst case? Using $\Theta$-notation, give the average-case and worse-case running times of linear search. Justify your answers.

**Problem 4**. How can you modify any sorting algorithm to have a good best-case running time?

## 2.3 Designing algorithms

**Problem 1**. Using *Figure 2.4* as a model, illustrate the operation of merge sort on an array initially containing the sequence $\langle3,41,52,26,38,57,9,49\rangle$.

**Problem 2**. The test in line 1 of the `Merge-Sort` procedure reads "**if** $p\geq r$" rather than "**if** $p\neq r$". If `Merge-Sort` is called with $p>r$, then the sub array $A[p:r]$ is empty. Argue that as long as the initial call of `Merge-Sort`$(A,1,n)$ has $n\geq1$, the test "**If** $p\neq r$" suffices to ensure that no recursive call has $p>r$.

**Problem 3**. State a loop invariant for the **while** loop of lines 12-18 of the `Merge` procedure. Show how to use it, along with the while loops of lines 20-23 and 24-27, to prove that the `Merge` procedure is correct.

**Problem 4**. Use mathematical induction to show that when $n\geq2$ is an exact power of 2, the solution of the recurrence

$$T(n)=\begin{cases}
2&&&\text{if } n=2\\
2T&&&\text{if } n>2
\end{cases}
$$

is $T(n)=n\lg{n}$.

**Problem 5**. You can also think of insertion sort as a recursion algorithm. In order to sort $A[1:n]$, recursively sort the sub array $A[1:n-1]$ and then insert $A[n]$ into the sorted sub array $A[1:n-1]$. Write the pseudo code for this recursive version of insertion sort. Give a recurrence for it's worst-case running time.

**Problem 6**. Referring back to the searching problem *(see Exercise 2.1-4)*, observe that if the sub array being searched is already sorted, the searching algorithm can check the midpoint of the sub array against $v$ and eliminate half of the sub array from further consideration. The **binary search** algorithm repeats this procedure, halving size of the remaining portion of the sub array each time. Write pseudo code, either iterative or recursive, for the binary search. Argue that the worst-case running time of binary search is $\Theta(\lg{n})$.

**Problem 7**. The **while** loop of lines 5-7 of the `Insertion-Sort` procedure in Section 2.1 uses a linear search to scan (backward) through the sorted sub array $A[1:j-1]$. What if insertion sort used a binary search *(see Exercise 2.3-6)* instead of a linear search? Would that improve the overall worst-case running time of insertion sort to $\Theta(n\lg{n})$?

**Problem 8**. Describe an algorithm that, given a set $S$ of $n$ integers and another integer $x$, determines whether $S$ contains two elements that sum to exactly $x$. Your algorithm should take $\Theta(n\lg{n})$ time in worst case.

## 2. Review
**Problem 1**. Insertion sort on small arrays in merge sort

Although merge sorts runs in $\Theta(n\lg{n})$ worst-case time and insertion sort runs in $\Theta(n^2)$ worst-case time, the constant factors in insertion sort can make it faster in practice for small problem sizes on many machines. Thus it makes sense to **coarsen** the leaves of the recursion by using insertion sort within merge sort when sub problems become sufficiently small. Consider a modification to merge sort in which $n/k$ sub lists of length $k$ are sorted using insertion sort and then merged using the standard merging mechanism, where $k$ is a value to be determined.

**Part A**. Show that the insertion sort can sort the $n/k$ sub lists, each of length $k$, in $\Theta(nk)$ worst-case time.
   
**Part B**. Show how to merge the sub lists in $\Theta(n\lg{(n/k)})$ worst-case time.
   
**Part C**. Given that the modified algorithm runs in $\Theta(nk+n\lg{(n/k)})$ worst-case time, what is the largest value of $k$ as a function of $n$ for which the modified algorithm has the same running time as standard merge sort, in terms of $\Theta$-notation?
**Part D**. How should you choose $k$ in practice?

**Problem 2**. Correctness of bubble sort

Bubble sort is a popular, but inefficient, sorting algorithm. It works by repeatedly swapping adjacent elements that are out of order. The procedure `BubbleSort` sorts array $A[1:n]$.

```pseudo
\begin{algorithm}
\caption{Bubble sort}
\begin{algorithmic}
  \Procedure{BubbleSort}{$A, n$}
	\For{$i \gets 1$ \To $n-1$}
		\For{$j \gets n$ \DownTo $i+1$}
			\If{$A[j]<A[j-1]$}
			\State exchange $A[j]$ with $A[j-1]$
			\EndIf
		\EndFor
	\EndFor
  \EndProcedure
\end{algorithmic}
\end{algorithm}
```

**Part A**. Let $A'$ denote the array $A$ after `BubbleSort`$(A,n)$ is executed. To prove that `BubbleSort` is correct, you need to prove that it terminates and that 

$$A'[1]\leq A'[2]\leq A'[3]\leq \dots\leq A'[n]$$
In order to show that `BubbleSort` actually sorts, what else do you need to prove?

**Part B**. State precisely a loop invariant for the **for** loop in lines 2-4, and prove that this loop invariant holds. Your proof should use the structure of the loop-invariant proof presented in this chapter.

**Part C**. Using the termination condition of the loop invariant proved in *part B*, state a loop invariant for the **for** loop in lines 1-4 that allows you to prove inequality in *part A*. Your proof should use the structure of the loop-invariant proof presented in this chapter.

**Part D**. What is the worst-case running time of the `BubbleSort`? How does it compare with the running time of `InsertionSort`?

**Problem 3**. *Correctness of Horner's rule*

You are given the coefficients $a_0,a_1,a_2,\dots,a_n$ of a polynomial

$$P(x)=\sum^{n}_{k=0}{a_kx^k}=a_0+a_1x+a_2x^2+\dots+a_nx^n$$

and you want to evaluate this polynomial for a given value of $x$. Horner's rule says to evaluate the polynomial according to this parenthesization:

$$
P(x)=a_0+x\Big(a_1+x\big(a_2+\dots+x(a_{n-1}+xa_n)\dots\big)\Big)
$$

The procedure `Horner` implements Horner's rule to evaluate $P(x)$, given the coefficients $a_0,a_1,a_2,\dots,a_n$ in an array $A[0:n]$ and the value of $x$.

```pseudo
\begin{algorithm}
\caption{Horner}
\begin{algorithmic}
\Procedure{Horner}{$A,n,x$}
	\State $p=0$
	\For{$i\gets n$ $\textbf{downto}$ $0$}
		\State $p=A[i]+x\cdot p$
	\EndFor
	\Return p
\EndProcedure
\end{algorithmic}
\end{algorithm}
```

**Part A**. In terms of $\Theta$-notation, what is the running time of this procedure?

**Part B**. Write pseudo code to implement the naive polynomial-evaluation algorithm that computes each term of the polynomial from scratch. What is the running time of this algorithm? How does it compare with `Horner`?

**Part C**. Consider the following loop invariant for the procedure `Horner`:

At the start of each iteration of the **for** loop of lines 2-3:
$$
p=\sum^{n-(i+1)}_{k=0}{A[k+i+1]\cdot x^k}
$$

Interpret a summation with no terms as equaling 0. Following the structure of the loop-invariant proof presented in this chapter, use this loop invariant to show that, at termination, $p=\sum^{n}_{k=0}{A[k]\cdot x^k}$.

**Solution to C**.

**Initialization**. Show that the loop invariant holds before the first loop iteration, when $i=n$. It is trivial that that the summation has no terms which implies $p=0$.

**Maintenance**. From the loop invariant, for any arbitrary $0\leq i<n$, at the start of the $i$-th iteration of the **For** loop of lines 2-3, $p=\sum^{n-(i+1)}_{k=0}{A[k+i+1]\cdot x^k}$. After $i$-th iteration, as we iterate from $n$ **downto** $0$, we will have $i=i-1$. So to prove the maintenance of the loop invariant, we'll need to show that after the $i$-th iteration, this equation holds:

$$
p=\sum^{n-((i-1)+1)}_{k=0}{A[k+(i-1)+1]\cdot x^k}=\sum^{n-i}_{k=0}{A[k+i]\cdot x^k}
$$

which can be shown by the following

$$\begin{align}
p' &= A[i]+x\cdot p\\
&= A[i]+x\cdot\sum^{n-(i+1)}_{k=0}{A[k+i+1]\cdot x^k}\\
&= A[i]+\sum^{n-(i+1)}_{k=0}{A[k+i+1]\cdot x^{k+1}}\\
&= A[i]x^0+A[i+1]x^1+A[i+2]x^2+\dots+A[n]x^{n-1}\\
&= \sum^{n-i}_{k=0}A[k+i]x^k
\end{align}$$


**Termination**. When the loop terminates, $n=0 \rightarrow i=-1$, which results in:

$$\begin{align}
p &= \sum^{n-(i+1)}_{k=0}A[k+i+1]x^k\\
&= \sum^{n-(-1+1)}_{k=0}A[k-1+1]x^k\\
&= \sum^{n}_{k=0}A[k]x^k
\end{align}$$

Which is precisely what we want to calculate.

**Problem 4**. *Inversions*

Let $A[1:n]$ be an array of $n$ distinct numbers. If $i<j$ and $A[i]>A[j]$, then the pair $(i,j)$ is called an **inversion** of $A$.

**Part A**. List five inversions of the array $\langle2,3,8,6,1\rangle$.

**Part B**. What array with elements from the set $\langle1,2,\dots,n\rangle$ has the most inversions? How many does it have?

**Part C**. What is the relationship between the running time of insertion sort and the number of inversions in the input array? Justify your answer.

**Part D**. Give an algorithm that determines the number of inversions in any permutation on $n$ elements in $\Theta(n\lg{n})$ worst-case time. *(Hint: Modify merge sort)*



