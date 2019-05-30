# Data structures and algorithms.
My notes and resources while studying data structures and algorithms.
I'll be adding better notes and hopefully pseudo code for every algorithm.

# Practice.
 - https://www.teamblind.com/article/New-Year-Gift---Curated-List-of-Top-100-LeetCode-Questions-to-Save-Your-Time-OaM1orEU
 - https://www.interviewcake.com/ (Paid)

# Types of algorithms
References and resources:
- https://quizlet.com/396658039/big-o-quick-reference-flash-cards/
- https://www.cis.upenn.edu/~matuszek/cit594-2003/Lectures/35-algorithm-types.ppt
- Halim, Steven, and Felix Halim. Competitive Programming: The New Lower Bound of Programming Contests. Lulu, 2013.
  (https://www.quora.com/What-are-the-different-types-of-Algorithms)
http://www.algorithmist.com/index.php/Main_Page
- Useful visualization tool: https://www.cs.usfca.edu/~galles/visualization/Heap.html 
- Big-O introduction: https://www.youtube.com/watchv=__vX2sjlpXU&list=PL9xmBV_5YoZMxejjIyFHWa-4nKg6sdoIv
- Big O analysis and cheatsheet: http://bigocheatsheet.com/ 

If GitHub doesn't render the notebook use https://nbviewer.jupyter.org/. I'll eventually just set up README's with links in each directory of type of algorithm.
  
# Algorithms types considered below:
 - Simple recursive algorithms
 - Backtracking algorithms
 - Divide and conquer algorithms
 - Dynamic programming algorithms
 - Greedy algorithms
 - Branch and bound algorithms
 - Brute force algorithms
 - Randomized algorithms

---

# Simple recursive algorithms:
 - Solves the base cases directly
 - Recurs with a simple subproblem
 - Does some extra work to convert the solution to the simpler  subproblem into a solution to the given problem.

Examples:
 - To count the number of elements in a list:
 - To test if a value occurs in a list.

# Backtracking algorithms

These algorithms are based on a depth-first recursive search:
 - Test to see if a solution has been found, and if so, returns it otherwise
 - For each choice that can be made at this point,
   - Make that choice
   - Recur
   - If the recursion returns a solution, return it
 - If no choices reamin, return failure
 
Example:
Color a map with no more than four colors.

color (Country n)
 - If all countries have been colored(n > number of countries) return success; otherwise,
 - For each color c of four colors,
   - If country n i s not adjacent to a country that has been colored c
     - Color country n with color c
     - recursively color country n+1
     - If successful, return success
   - Return failure (if loop exits)
  
# Divide and conquer algorithms

Method that divides the problem into smaller parts and then solving those parts. Think binary search.

--- 

A divide and conquer algorithm consists of two parts:
 - Divide the problem into smaller subproblems of the same type, and solve these subproblems recursively
 - Combine the soutions to the subproblems into a soution to the original problem
 
Traditionally, an algorithm is only called divide and conquer if it contains two or more recursive calls.

Examples:
Quicksort:
 - Partition the array into two parts, and quicksort each of the parts
 - No additional work is required to combine the two sorted parts
 
Mergesort:
 - Cut the array in half, and mergesort each half
 - Combine the two sorted arrays into a single sorted array by merging them

# Dynamic programming algorithms

Method that builds up to a solution using previously found sub-solutions. Definitely one of the more advanced techniques, but extremely powerful and applicable.
 - Pros: finds the optimal solution to many problems in polynomial time (whereas brute force would take exponential)
 - Cons: difficult to grasp and apply, takes time to understand the various states and recurrence

---

A dynamic programming algorithm remembers past results and uses them to find new results.

Dynamic programming is gernally used for optimization problems.
 - Multiple soutions exist to find the "best one"
 - Requires "optimal substructure" and " overlapping subproblems"
   - Optimal subtructure: Optimal solution contains optimal solutions to subproblems
   - Overlapping subproblems: Solutions to subproblems can be stored and reused in a bottom-up fashion.
   
This differes from Divide and Conquer, where subproblems genrally need not overlap.

# Greedy algorithms

Method that chooses the best option at the current time, without any consideration for the future.
 - Pros: quick, simple, may obtain the best solution, or get kinda close
 - Cons: most of the time, we will not obtain the best solution

--- 

An optimization problem is one in which you want to find, not just *a* solution, but the best *solution*.

A "greedy algorithm sometimes works well for optimization problems.

A greedy algorithm works in phases; at each phase:
 - You take the best you can get right now, without regard for future consequences
 - You hope that by choosing a local optimum at each step, you will end up at a global optimum.
 
Example:
Counting money

Supposed you want to count out a certain amount of money, using the fewest possinble bill and coins.

A greedy algorithm would do this would be:
At each step, take the largest possible bill or coin that does not overshoot.
 - Example: To make `$6.39`, you can choose:
   - A `$5` bill
   - A `$1` bill to make `$6`
   - A `25¢` coin to make `$6.25`
   - A `10¢` coin, to make `$6.35`
   - Four `1¢` coins to make `$6.39`
   
For U.S. money, the greedy algorithm always gives the optimum solution.

A failure of the greedy algorithm:
In some (fictional monetary system, "Krons" come in 1, 7 and 10 Kron coins.

Using a greedy algorithm to count out `15 Krons` you would get:
   - A `10 Kron` coin
   - Five `1 Kron` coins totalling to `15 Krons`. This requres six coins
   
A better solution would be to use two `7 Kron` coins and a `1 Kron` coin.

The greedy algorithm results in a solution but not in an optimal solution.

# Branch and bound algorithms

Branch and bound algorithms are generally used for optimization problems.
 - As the algorithm progresses, a tree of subproblems is formed
 - The original problem is considered the "root problem"
 - A method is used to construct an upper and lower bound for a given problem
 - At each node, apply thr bounding methods
   - If the bounds nath, it is deemed a fesadible soultion to that particular subproblem
   - If bounds do *not* matchm partition the problem represented by that node, and make the two subproblems into children nodes
 - Continue, using the best known feasible solution to trim sections of the tree, until all nodes have been solved or trimmed
 
Example:

Traveling salesman problem: A salesman has to visit each of n cities (at least) once each, and wants to minimize total distance travelled.
 - Consider the root problem to be the problem of finidng the shortest route through a set of cities visiting each city once
 - split the node into two child problems:
   - Shortest route visiting city `A` first
   - Shortest route *not* visiting city `A` first
 - Continue subdividing similarily as the tree grows

# Brute force algorithms/Complete search:

A method that looks at all the possibilities and selects the best solution.
 - Pros: simple, should always find the solution since you are looking at every possibility
 - Cons: infeasible as the number of possibilities grows exponentially as the number of items increases
---

A brute force algorithm simpluy tries all possibilities until a satisfactory solution is found.

- Such an algorithm can be:
  - Optimizing: Find the best solution. This may require finding all solutions, or if a value for the best solution is knwon, it may stop when any best solution is found
    - Example: Finding the best path for a travelling salesman
  - Satisficing: Stop as soon aas a so,ution is foun that is *good enough*
    - Example: Finding a travelling salesman path that is within 10% optimal
    
Improving brute force algorithms:
 - Often brute force algorithms require exponential time
 - Various *heuristics* and *optimizations* can be used
   - Heuristic: A "rule of thumb" that helps you decide which possibilities to look at first
   - Optimization: In this case, a way to eliminate certain possibilites without fully exploring them
 
# Randomized algorithms

A randomized algorithm uses a random number at least once during the computation to make a decision:
 - Example: In quicksort, using a random number to choose a pivot
 - Example: Trying to factor a large prime by choosing random numbers as possible divisors
