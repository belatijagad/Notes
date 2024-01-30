[[Design & Analysis of Algorithms]]

---

## What is loop invariant?
Loop invariant help us understand why an algorithm is correct. When using loop invariant, there are three things that needs to be proven:

**Initialization**. It is true prior to the first iteration of the loop.

**Maintenance**. If it is true before an iteration of the loop, it remains true before the next iteration.

**Termination**. The loop terminates, and when it terminates, the invariant--usually along with the reason that the loop terminated--gives us a useful property that helps show that the algorithm is correct.

When the first two properties hold, the loop invariant is true to every iteration of the loop. A loop-invariant proof is a form of **mathematical induction**, where to prove that a property holds, you prove a base case and an inductive step. 

- Showing that the invariant holds before the first iteration corresponds to the base case.
- Showing that the invariant holds from iteration to iteration corresponds to the inductive step.

The third property is the most important one, since loop invariant is used to prove correctness. Typically, loop invariant is used along with the condition that caused the loop to terminate. Mathematical induction typically applies the inductive step infinitely, but in a loop invariant, the "induction" stops when the loop terminates.

## Example: `Insertion-Sort`

```pseudo
\begin{algorithm}
\caption{InsertionSort}
\begin{algorithmic}
\Procedure{InsertionSort}{$A,n$}
	\For{$i\gets2$ \To $n$}
		\State $key=A[i]$
		\State // Insert A[i] to the sorted sub array A[1:i-1]
		\State $j=i-1$
		\While{$j>0$ \And $A[j]>key$}
			\State $A[j+1]=A[j]$
			\State $j=j-1$
		\EndWhile
		\State $A[j+1]=key$
	\EndFor
\EndProcedure
\end{algorithmic}
\end{algorithm}
```

**Initialization**. Show that the loop invariant holds before the first loop iteration, when $i=2$.  The sub array $A[1:i-1]$ consists of just the single element $A[1]$, which is in fact the original element in $A[1]$. Moreover, this sub array is sorted which shows the loop invariant holds prior to the first iteration of the loop.

**Maintenance**. Next, it must be shown that each iteration maintains the loop invariant. Informally, the body of the **for** loop works by moving the values in $A[i-1]$, $A[i-2]$, $A[i-3]$, and so on by one position to the right until it finds the proper position for $A[i]$, at which point it inserts the value of $A[i]$. The sub array $A[1:i]$ then consists of the elements originally in $A[1:i]$, but in sorted order. **Incrementing** $i$ for the next iteration of the **for** loop then preserve the loop invariant.

A more formal treatment of the second property would require us to state and show a loop invariant for the **while** loop.

**Termination**. The loop variable $i$ starts at 2 and increases by 1 in each iteration. Once $i$'s value exceeds $n$, the loop terminates. Substituting $n+1$ for $i$ in the wording of the loop invariant yields that the sub array $A[1:n]$ consists of the elements originally in $A[1:n]$, but in sorted order. Hence, the algorithm is correct.