

**Problem 1**. Write a problem statement of a given problem and give an instance of the input and output.

0/1 Knapsack Problem

Shortest Part Problem (eg: Dijkstra algorithm)

**Problem 2**. Compare list and dictionary data structure. Write a condition where one is suitable for the task while the other aren't.

**Solution**. List is a data structure where, while dictionary is a data structure that maps a value to a given location based on the hashing function. 

**Problem 3** *\[CLRS Exercise 1.2-2\]*. Suppose we are comparing implementations of insertion sort and merge sort on the same machine. For input of size $n$, insertion sort runs at $8n^2$ steps, while merge sort runs in $64n\lg{n}$ steps. For which values of $n$ does insertion sort **beats** merge sort?

**Solution**. For insertion to beat merge sort, it's steps must be strictly smaller than merge sort's steps.

$$\begin{align}
8n^2 &< 64n\lg{n}\\
n&<8\lg{n}
\end{align}$$
By solving the equation $n-8\lg{n}=0$, the value $n\approx43.5593$ will be get. So for insertion sort to beat merge sort, it must satisfy the condition $n<43.5593$.

**Problem 4** *\[CLRS Problem 1.1\]*. For each function $f(n)$ and time $t$ in the following table, determine the largest size $n$ of a problem that can be solved in time $t$, assuming that the algorithm to solve the problem takes $f(n)$ miliseconds.