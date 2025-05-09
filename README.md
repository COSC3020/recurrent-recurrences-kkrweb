# Recurrent Recurrences

Give big $\Theta$ bounds for the following recurrence relations.

1.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        T\left(\frac{n}{13}\right) + 5 & n > 1
    \end{cases}
$$

2.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        13 T\left(\frac{n}{13}\right) + 5 & n > 1
    \end{cases}
$$

3.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        13 T\left(\frac{n}{13}\right) + 2n & n > 1
    \end{cases}
$$


//


Name: Kane Kriz

Start Date: 12 Feb 2025

Last Edited: 9 April 2025

Feedback Request 1 Date: 9 April 2025


//


**Response Part 1, Recurrence Relation 1:**

(Using substitution method)

The base case occurs when n ≤ 1.

When the base case condition is met, the function returns in constant time, giving us $T(n) = 1$.

For the case where n > 1, the function makes a single recursive call to $T(n/13)$.

Additionally, a constant amount of work is performed (+ 5).

Next we can expand the recurrence using substitution.

The first expansion gives us $T(n) = T(n/13) + 5$. 

Substituting again, we get $T(n) = [T(n/13^2) + 5] + 5 = T(n/13^2) + 2 * 5$

Observing this substitution pattern after i substitutions, the recurrence relation is $T(n) = T(n/13^i) + 5 * i$.

The recursion continues until we reach the base case, which occurs when $n/13^i ≤ 1$. 

We know the base case is observed at $n/13^i ≤ 1$ due to the recursive calls continually dividing n by 13 until the problem size becomes 1 or smaller, which triggers the base case condition where the function returns immediately.

Solving for i, this occurs at $i = \log_{13} n$.

At this point, we can express the complete expansion as $T(n) = T(1) + 5 * \log_{13} n = 1 + 5 * \log_{13} n$.

Within asymptotic analysis, the log term dominates that of the constant term, which becomes irrelevant.

The logarithm utilizing base 13 can be simplified into Θ(log n), as the base becomes irrelevant in big Theta asymptotic notation.

Due to this, the solution to recurrence relation 1 is: $T(n) ∈ Θ(log n)$.


//


**Response Part 2, Recurrence Relation 2:**

(Using substitution method)

The base case occurs when $n \leq 1$, where the function returns in constant time, giving us $T(n) = 1$.

For the recursive case where n > 1, the function makes 13 recursive calls to $T(n/13)$ while performing a constant amount of additional work (+5).

Next we can expand the recurrence via substitution.

The first expansion gives us $T(n) = 13T(n/13) + 5$.

Substituting again, we get $T(n) = 13[13T(n/13^2) + 5] + 5 = 13^2T(n/13^2) + 13*5 + 5$.

Continuing this substitution pattern for after i substitutions, the recurrence relation is $T(n) = 13^i T(n/13^i) + 5 \sum_{k=0}^{i-1} 13^k$.

The recursion continues until we reach the base case, which occurs when $n/13^i \leq 1$.

The base case is observed at $n/13^i \leq 1$ due to the recursive calls continually dividing n by 13 until the problem size becomes 1 or smaller, which triggers the base case condition where the function returns immediately.

Solving for i, this occurs at $i = \log_{13} n$.

At this point, the expansion is now: $T(n) = 13^{\log_{13} n} * 1 + 5*[(13^{\log_{13} n} - 1)/12] = n + (5/12)(n - 1)$.

For asymptotic analysis, the linear term dominates that of the constant terms, which become irrelevant.

Due to this, the solution to recurrence relation 2 is: $T(n) ∈ Θ(n)$.


//


**Response Part 3, Recurrence Relation 3:**

(Using substitution method)

The base case occurs when $n \leq 1$, where the function returns in constant time, giving us $T(n) = 1$. 

For the recursive case where $n > 1$, the function makes 13 recursive calls to $T(n/13)$ while performing linear work corresponding to the input size (2n work).

Next we can expand the recurrence via substitution.

The first expansion gives $T(n) = 13T(n/13) + 2n$. 

Substituting again yields $T(n) = 13[13T(n/13^2) + 2(n/13)] + 2n = 13^2T(n/13^2) + 2n + 2n$.

Continuing this pattern for after i substitutions, the relation becomes $T(n) = 13^i T(n/13^i) + 2n * i$.

The recursion progresses until reaching the base case condition $n/13^i \leq 1$, which occurs when $i = \log_{13} n$ since each recursive call reduces the problem size by a factor of 13. 

At this point, the expansion is $T(n) = 13^{\log_{13} n} * 1 + 2n\log_{13} n = n + 2n\log_{13} n$.

In asymptotic analysis, the $n\log_{13} n$ term dominates the linear $n$ term. 

The additional coefficient 2 for this recurrence relation is a constant factor, and thus is irrelevant in computing asymptotic work due to the prescence of linear and log terms.

Therefore, the solution to recurrence relation 3 is: $T(n) \in Θ(n * log n)$.


//


Plagiarism Acknowledgement: I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.


Citations:

github LaTeX formatting documentation, provided from the other exercises.

“Substitution Method to Solve Recurrence Relations.” GeeksforGeeks, 18 Mar. 2024, www.geeksforgeeks.org/substitution-method-to-solve-recurrence-relations/.

For help with substitution logic and notation where applicable: 
Su, Jessica. CS 161 Lecture 3. https://web.stanford.edu/class/archive/cs/cs161/cs161.1168/lecture3.pdf
