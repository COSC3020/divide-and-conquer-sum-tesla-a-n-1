# Divide and Conquer Sum

In the lectures, we've covered merge sort, which uses a divide-and-conquer
approach to sort an array of values. There are many more algorithms that take
such an approach. Implement a function that computes the sum of an array of
integers using divide and conquer, using the template in `code.js`. Test your
new function; I've provided some basic testing code that uses
[jsverify](https://jsverify.github.io/) in `code.test.js`.

The recursive calls sum up the numbers in the base case, and "merges" the sums
of the recursive calls otherwise. For example, the return value for the array `a
= [1,5,-1,4]` is `9`.

To make it a bit more interesting, instead of splitting into two sub-arrays like
in merge sort, I want you to split into *three* sub-arrays at each divide step.

Hint: Like in the implementation of merge sort, you may need a helper function
that does the actual recursion.

## Runtime Analysis

What is the runtime of the algorithm that you implemented? Provide a recurrence
relation for $T(n)$ as we did for merge sort (you can ignore constant factors)
and solve it as we did in the lectures. Give the final $\Theta$ complexity.

Describe your reasoning and the conclusion you've come to. Your reasoning is the
most important part. Add your answer to this markdown file.

Let T(n) be the time complexity for sorting an array of size n.

The algorithm Divides, Conquers, and then Combines the array(s)

The combining of elements or merging of elements happens recursively by adding the results
at each recursive level.

     If the array is empty, it returns 0 because there are no elements to sum,
     
     if the array has one element, it returns that element as the sum
     
     if the array has two elements, it returns the sum of those two integers as a basecase
     to avoid further splitting.
     
     After the subarrays are divided, each element is merged with what is left in the 
     left, mid, or right subarray, accumulating the sum until the origional array's sum
     is calculated at the top level.
     
Divide splits the array into 3 sub-arrays about n/3 in size uses constant time O(1)

Conquer recursively sorts the three sub-arrays so 3*T(n/3)

Merging the split subarrays requires 2 additions, whcih is O(1) or a constant c

T(n) = 1 if n <= 2 or T(n) = 3T(n/3) + n if n > 2

     = 3 [ 3T(n/9) + n/3 ] + c
     
     = 9T(n/9) + 3c + c

     = 9T(n/9) + 4c

     ...

     = 27T(n/27) + (3^i-1)c/(3-1)

     = 3^(3)T(n/3^(3)) + (3^i-1)c/2

     for i = $log(base 3)n //should be $log(base 3)n$ not lg(n)

     T(n) = $3^(log(base 3)(n))T(1) + (3^(log(base 3)(n))-1)c/2

     with T(1) as a constant, simplifies to 

     $\in$ $\Theta(n)$ + $\Theta(log(n))$

     since the linear term dominates the logarithmic term, 

     = $\Theta(n)

After revising, solving the T(n) recurrence relation gives a complexity of T(n) $\in$ $\Theta(n)$ which shows the algorithm's time complexity grows at the same rate as n.

Sources: https://www.w3schools.com/jsref/jsref_reduce.asp for reduce knowledge and syntax help

"I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice." This was my submission from last semester altered
