Download Link: https://assignmentchef.com/product/solved-ece3790-lab2-divide-and-conquer
<br>
<strong>The purpose of this lab is to give you practical experience programming and analyzing recursive algorithms, specifically divide-and-conquer algorithms.</strong>

<strong>Important: </strong>Please include the following signed statement with your submission.

I (We), [insert name(s)] attest that the work I am (we are) submitting is my (our) own work and that it has not been copied/plagiarized from online or other sources. Any sourced material used for completing this work has been properly cited. [Signature(s)]

<strong>Also Important: </strong>Labs done in pairs must be submitted with a short paragraph outlining each partner’s contribution.

<h1>Introduction</h1>

So far in the course we have seen a handful of divide-and-conquer algorithms: merge sort, the maximum-subarray problem, tower of Hanoi, and recursive matrix multiplication. Each of these leads to a recurrence relation of the form:

<em>T</em>(<em>n</em>) = <em>D</em>(<em>n</em>) + <em>aT</em>(<em>n/b</em>) + <em>C</em>(<em>n</em>)<em>,                                             </em>(2.1)

with a base case

<em>T</em>(<em>n</em><sub>0</sub>) = <em>B</em>(<em>n</em><sub>0</sub>)<em>,</em>

where we have divided the problem of size <em>n </em>into <em>a </em>pieces of size <em>n/b</em>. <em>D</em>(<em>n</em>) is the time (or operation count) to divide the problem, <em>C</em>(<em>n</em>) is the time to combine the subproblems, and <em>n</em><sub>0 </sub>is some base case size that requires a constant number of operations <em>B</em>(<em>n</em><sub>0</sub>). Note that here <em>n</em><sub>0 </sub>is just a constant problem size and should not be confused with the <em>n</em><sub>0 </sub>required for asymptotic notation definitions.

In class we have also learned a few techniques for solving recurrences (substitution method, recursion trees, master method) and as clever ECE 3790 students I’m sure you’re all looking for a convenient (i.e., easy) way to check your solutions to those recurrences. Well, why don’t we just program a recursive evaluation of the recurrence in equation (1) and use that to check if our answers make sense throughout the course? To make sure it works we can implement a recursive algorithm, say recursive block matrix multiplication, and see how well it predicts performance compared to actual performance.

<strong>Notes: </strong>This lab requires both programming and “on-paper” work. For this lab, you are only required to implement solutions in one language of your choice (Python, Java, C/C++, Matlab).

<h1>Problem 1 – Recurrence Relations</h1>

<h2>Functions</h2>

Implement a function called evaluaterecurrence that takes as input a vector of integers nvec and returns the total cost of evaluating a divide-and-conquer algorithm by evaluating some recurrence relation for each value of <em>n </em>in nvec. The goal is to determine the costs of evaluating a divide-and-conquer algorithms for different input sizes without actually running the algorithm. There are a couple of ways to approach this:

<ol>

 <li>You have evaluaterecurrence call a hard-coded function that describes the recurrence of interest.</li>

 <li>You pass evaluaterecurrence a function pointer so that it can evaluate any recurrence relation just by being passed the appropriate function.</li>

</ol>

The most general-purpose approach is to use function pointers/handles. <strong>In this lab we require function pointers/handles for successful implementation, i.e., full marks.</strong>

In case we are confused as to what needs to happen here, we are aiming to write a function that we can call as follows:

costs = evaluaterecurrence(myfunction, nvec)

where we want to evaluate myfunction(n) for each entry in the vector nvec. The function myfunction will, in general, calculate

value = D(n) + a*T(n/b) + C(n)

and return value. For example the function you write could be mergesortrecurrence(n) which, in the recursive case, returns value = 1 + 2*mergesortrecurrence(n/2) + n.

Note:

<ul>

 <li>You will have to write an appropriate base case for each recurrence into your recurrence function.</li>

 <li>It is not necessary for your solution to be exact. For example it is possible to use floors/ceilings to your advantage in order to approximate the answers. Of course you could also be very precise in the way you code things up. You will be asked about any assumptions you made in the discussion.</li>

 <li>You are free to add any function arguments you need if they help.</li>

</ul>

<h2>Main Program</h2>

Write a main program Lab 2 Problem 1 that specifies an array of values of <em>n </em>in nvec and uses your function(s) to evaluate and plot the cost trends as a function of <em>n </em>for the following recurrence relations:

<ol>

 <li><em>T</em><sub>1</sub>(<em>n</em>) = 1 + 2<em>T</em>(<em>n/</em>2) + <em>n </em>(Merge Sort)</li>

 <li><em>T</em><sub>2</sub>(<em>n</em>) = 2<em>T</em>(<em>n </em>− 1) + 1 (Tower of Hanoi)</li>

 <li><em>T</em><sub>3</sub>(<em>n</em>) = 5<em>T</em>(<em>n/</em>3) + <em>n</em></li>

 <li>The cost of a recursive algorithm of your choosing that has not yet been covered in class (research, references, and an algorithm explanation required).</li>

</ol>

<h2>Data Collection and Analysis</h2>

Once you have completed writing your function and main program you need to:

<ul>

 <li>Call your main program on appropriate values of <em>n </em>to get the general trends of the recurrence relations (use your judgement to determine the ranges of <em>n </em>used so that you see the correct trend).</li>

 <li>Determine a closed-form (tight) asymptotic bound (upper or lower depending perhaps on what is convenient) for each of the 4 recurrence relations. If we have done a derivation in class then feel free to use the result (with reference). Otherwise we need a more-or-less complete proof. <strong>Note</strong>: that your code may be a good way to establish a guess instead of using recursion trees!</li>

 <li>For each of the 4 recurrences, plot the analytic solutions and the output of the main program in one figure, producing 4 total plots. Make sure to scale the curves (using a single multiplying factor) so that they line up for large values of <em>n</em>. Do this dynamically based on your data – do <strong>not </strong>scale by some arbitrary large constant. Make sure that a figure legend shows exactly what constant you are multiplying by and your closed-form function.</li>

</ul>

<h2>Evaluation and Discussion</h2>

Answer the following questions:

<ol>

 <li>What assumptions, if any, did you make in coding up the solutions to the recurrence relations?</li>

 <li>For each of the four recurrences briefly discuss whether or not your analytic solution and numerical solution agree. If they do not, do your best to explain what is going on.</li>

 <li>In order to line up the plots it is necessary to scale the results. Why is this an acceptable thing to do? How did you go about doing this?</li>

 <li>Have you gained any intuition in analyzing recurrences from this exercise? That is, from the 4 recurrences given, can you summarize how features of the equation affect the change in asymptotic growth?</li>

 <li>What base cases did you implement for each of the recurrences and why? For one of the recurrences try changing the base case. Does it change the overall trend? Why or why not?</li>

</ol>

<h2>Bonus</h2>

Evaluating functions recursively generally requires more overhead than is actually necessary: we have to push the state of the program to the stack every time we make a function call. It turns out that we can usually implement recursive programs without actually making recursive calls using either a stack or a queue. Describe and provide pseudocode for a technique that would replace your recursive function in this problem with an alternative method using a queue or stack (think about which one is appropriate here). If you really want to impress us, then implement it and show it gives the same results as your recursive program.

<strong>Hand in:</strong>

Hand in your derivations for the recurrence relation solutions, all code, plots, and your answers to the discussion questions.

<h1>Problem 2 – Recursive Matrix Multiplication</h1>

<h2>Functions</h2>

Implement a recursive block matrix multiplication function recursivematrixmultiply that takes as arguments matrices A and B as well as a minimum block size and produces the product C = A*B recursively, using automatic block partitioning into 4 blocks of roughly equal size. Details can be found in Lecture 9. The following notes apply:

<ul>

 <li>It is likely beneficial to pass the output <em>C </em>as a reference argument (depending on your language) so that you can update it as you go.</li>

 <li>An efficient solution to this problem will <u>not </u>copy submatrices but use indexes to appropriately offset into the matrices without copying. <strong>For full marks, your solution should use indexing and not copy the submatrices</strong>.</li>

 <li>It is not necessary for the matrices to be square.</li>

 <li>Your function should identify and report erroneous problem instances.</li>

 <li>You are free to add any function arguments required for your language of choice (e.g., sizes and block offsets).</li>

 <li>You can use derived types or classes to represent matrices but will have to clearly explain what you’re using and where it comes from (if you’re using a third-party</li>

</ul>

library)

<h2>Main Program</h2>

Write a main program Lab 2 Problem 2 that:

<ul>

 <li>Reads the sizes of matrices A and B from the command line (or other user input), allocates and fills A and B as random matrices, and recursively evaluates the product C = A*B.</li>

 <li>Evaluates the computational time of the matrix product (excluding other operations) and clearly displays the elapsed time.</li>

 <li>Verifies the matrix product (you can reuse anything you need from Lab 1).</li>

</ul>

<h2>Validation and Data Collection</h2>

Once you have completed writing your function and main program you need to:

<ul>

 <li>Show that your function works for both square and rectangular matrices (you will need to decide what is convincing).</li>

 <li>Use your function to collect timing data for various square matrix sizes, for example <em>n </em>= 100<em>,</em>200<em>,</em>400<em>,</em>800<em>,…</em>.</li>

 <li>Argue the mathematical expression for the recurrence relation for this function in your own words. i.e. explain what each coefficient and term in the relation <em>T</em>(<em>n</em>) = <em>D</em>(<em>n</em>) + <em>aT</em>(<em>n/b</em>) + <em>C</em>(<em>n</em>) for this algorithm.</li>

 <li>Use the results from Part 1 of this lab to verify that the recurrence relation agrees with the observed times. To do this, produce a plot showing the actual measured times, the times predicted from the recurrence, and the closed-form solution to the recurrence (you do not need to prove it) all appropriately scaled so they line up.</li>

 <li>Produce a plot comparing the run times of the recursive function to the non-recursive implementation from Lab 1. You can just reuse your numbers assuming you are on a computer with the same hardware as Lab 1, otherwise re-collect the Lab 1 results.</li>

</ul>

<h2>Evaluation and Discussion</h2>

Answer the following questions:

<ol>

 <li>How does your analysis of the algorithm performance compare with the measured results? Discuss.</li>

 <li>How does the performance of the recursive algorithm compare to the solution you implemented in Lab 1? What features of the algorithm/implementation contribute to the performance being either the same or different (depending on what you observe).</li>

 <li>Strassen’s algorithm improves upon the complexity of matrix multiplication by using a block matrix structure in addition to some clever substitutions. Briefly explain how Strassen’s algorithm improves on the complexity. Make sure to provide references for your answer.</li>

</ol>