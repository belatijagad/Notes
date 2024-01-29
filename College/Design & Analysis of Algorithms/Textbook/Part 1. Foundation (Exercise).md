## 1.1 Algorithms 
**Problem 1**. Describe your own real-world example that requires sorting. Describe one that requires finding the shortest distance between two points.

**Solution**. One sorting problem is when you want to find the highest scoring run on the runs you have done because it requires comparison between each run with another until a specific run is always higher than the other runs. Shortest distance problem is probably online taxi's maps, it shows the shortest legal path so it can determine the fare needed.

**Problem 2**. Other than speed, what other measures of efficiency might you need to consider in a real-world setting?

**Solution**. Memory usage is another measure of efficiency that needs to be considered. An algorithm could be fast, but expensive in memory because it needs to store caches in order to compute more efficiently.

**Problem 3**. Select a data structure that you have seen and discuss it's strengths and limitations.

**Solution**. One data structure that I often use is list. In python, it's basically a dinamically shaped array which can store as many objects needed. Because of that, I don't need to worry about resizing the list each time I add or remove items. While it's dynamically sized, the insertion and deletion complexity is $O(n)$ at worst, so it's not an efficient data structure if I only want to remove objects on the end of the list.

**Problem 4**. How are the shortest-path and traveling-salesperson problem given above similar? How are they different?

**Solution**. Shortest-path and travelling-salesperson are similar because both are searching for the smallest weight approach. The difference lies within the objectives themselves. Shortest-path only cares about the path with minimum weight to travel from the origin to the end node, while traveling-salesperson needs to find the path with minimum weight that visits *all* of the available nodes *then* return to the origin node, which means the solution must be a cycle.

**Problem 5**. Suggest a real-world problem in which only the best solution will do. Then come up with one in which "approximately" the best solution is good enough.

**Solution**. The problem that need the best solution is P (polynomial) problems such as sorting, while the one that only need the "approximately" best solution are NP-complete problems (stands for nondeterministic polynomials) such as traveling-salesperson problem.

**Problem 6**. Describe a real-world problem in which sometimes the entire input is available before you need to solve the problem, but other times the input is not entirely available in advance and arrives over time.

The only real-world problem I can imagine are time series problems where we need to predict something based on historic data.
## 1.2 Algorithms as technology

**Problem 1**. Give an example of an application that requires algorithmic content at the application level, and discuss the function of the algorithms involved.

One example is the automatic discount that is applied on GoJek application. It sorts the discount values first then find the one which have the largest discount value then automatically apply it on checkout.

**Problem 2**. Suppose that input of size $n$ on a particular computer, insertion sort runs in $8n^2$ steps and merge sort runs in $64n\lg{n}$ steps. For which value of $n$ does insertion sort beat merge sort?

**Solution**. For insertion to beat merge sort, it's steps must be strictly smaller than merge sort's steps.

$$\begin{align}
8n^2 &< 64n\lg{n}\\
n&<8\lg{n}
\end{align}$$

By solving the equation $n-8\lg{n}=0$, the value $n\approx43.5593$ will be get. So for insertion sort to beat merge sort, it must satisfy the condition $n<43.5593$.

**Problem 3**. What is the smallest value of $n$ such that algorithm whose running time is $100n^2$ runs faster than an algorithm whose running time is $2^n$ on the same machine?

**Solution**. Suppose that algorithm A is the one which have the running time of $100n^2$ while algorithm B is $2^n$.

$$\begin{align}
100n^2 &< 2^n\\
\lg{100n^2} &< \lg{2^n}\\
\lg{100}+2\lg{n} &< n
\end{align}$$

By solving the equation $\lg{100}+2\lg{n}-n=0$, the value $n\approx0.10365$ or $n\approx14.32472$ will be get. Because of it, $n$ must satisfy $0.10365<n<14.32472$ or simply $n<14.32472$ in order for algorithm A to outperform algorithm on the same machine.

**Problem 4**. For each function $f(n)$ and time $t$ in the following table, determine the largest size $n$ of a problem that can be solved in time $t$, assuming that the algorithm to solve the problem takes $f(n)$ microseconds.

|            | second | minute | hour | day | month | year | century |
|:----------:|:------:| ------ | ---- | --- | ----- | ---- | ------- |
|  $\lg{n}$  |        |        |      |     |       |      |         |
| $\sqrt{n}$ |        |        |      |     |       |      |         |
|    $n$     |        |        |      |     |       |      |         |
|   $n^2$    |        |        |      |     |       |      |         |
|   $n^3$    |        |        |      |     |       |      |         |
|   $2^n$    |        |        |      |     |       |      |         |
|    $n!$    |        |        |      |     |       |      |         |