![[28-final-review.pdf]]
![[28.1-final-review-solutions.pdf]]
Study the stuff listed on the exam review + some stuff from the packet whatever that is
it is:
For the core algorithms and data structures covered, be able to explain:
- What they do, how they work, and their asymptotic time complexities
- Relevant tradeoffs between different viable choices
- Their applications

## Iterative Algorithm Analysis
The basic operation is the operation that gets repeated the most often. Sometimes within the innermost loop OR the like if statement within a loop

Choose the one that's most cost:
1. Division
2. Multiplication
3. Add / Subtraction
4. Comparison
5. Variable Assignment

The size of the input is usually pretty intuitive. For example:
- Searches are array length
- Graphs are number of vertices and edges
- Strings are length
- ints are size

Usually found in the comments for the algorithm. Like the input is a string so you know the size is string length. Exceptions apply depending on the algorithm

Time complexity for basic iterative algorithms is usually just how many for loops there is

## Recursive Algorithm Analysis
## Exhaustive Search Algorithm Design
It's literally just checking ALL of it. Usually a lot of for loops with conditions in it. The time complexity for the entire algorithm is usually O(n^m) where n is the size and m is how many iterations over the list there is (usually 2)

The important question is if it's <mark style="background: #ADCCFFA6;">P (Polynomial time) or NP (Nondeterministic polynomial time)</mark>
Explanation from chatgpt:
- **Definition**: <mark style="background: #ADCCFFA6;">P</mark> is the class of problems that can be solved by a deterministic algorithm in polynomial time, i.e., the time taken to solve the problem grows at most as a polynomial function of the input size.
- **Significance**: Problems in P are considered "efficiently solvable." For example, sorting a list or finding the shortest path in a graph (using algorithms like Dijkstra's) are in P.
- **Example Problems**:
	- Sorting a list: $O(n \log n)$
	- Searching in a database: $O(\log n)$
	- Finding the shortest path in a graph: $O(n^2)$ or better.
- **Definition**: <mark style="background: #ADCCFFA6;">NP</mark> is the class of problems for which a solution, if given, can be verified in polynomial time by a deterministic algorithm. In other words, while we might not know how to solve the problem efficiently, we can quickly check if a proposed solution is correct.
- **Significance**: Many problems in NP are not known to be solvable efficiently, but verifying their solutions is efficient. This class includes many optimization and decision problems.
- **Example Problems**:
    - The Traveling Salesperson Problem (TSP): Given a route, you can quickly verify whether it meets the distance constraint.
    - Sudoku: Given a filled grid, you can quickly verify whether it satisfies the rules.

The debate is whether ALL P = NP which would mean any problem where a solution can be verified efficiently can be solved efficiently. Big deal and all that

<mark style="background: #ADCCFFA6;">NP-Complete</mark> means you found a polynomial time solution for a NP problem that proves this instance of NP = P
Examples: Traveling Salesperson Problem (decision version), Boolean Satisfiability Problem (SAT), Graph Coloring

## Pathfinding Algorithms
Basically just algorithm word vomit

| **Algorithm**      | **Implementation**                        | **Key Uses**                                                                     | **Time Complexity**                                                  | **Special Notes**                                       |
| ------------------ | ----------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------- | ------------------------------------------------------- |
| **DFS**            | Stack/Recursion                           | Exploring paths, cycle detection                                                 | No guarantee of optimality, linear or $O(\vert V\vert+\vert E\vert)$ | $O(V + E)$                                              |
| **BFS**            | Queue                                     | Shortest path in unweighted graphs                                               | Linear or $O(\vert V\vert + \vert E\vert)$                           | Ensures the shortest path in an unweighted graph.       |
| **Dijkstra’s**     | Priority Queue                            | With greedy selection, finds shortest path from a source node to all other nodes | $O( \vert E\vert \cdot \log{\vert V\vert})$                          | Only works with non-negative weights.                   |
| **A***             | Priority Queue + Admissible Heuristic     | Pathfinding with heuristics to a specific target node                            | $O( \vert E\vert \cdot \log{\vert V\vert})$                          | Requires nodes to have coordinates or something similar |
| **Floyd-Warshall** | 2D Array (DP Table) + dynamic programming | All-pairs shortest path                                                          | $\Theta(n^3)$                                                        | Handles negative weights but not negative cycles.       |
- **DFS/BFS**: When exploring or searching in unweighted graphs.
- **Dijkstra’s**: When finding a single-source shortest path in a graph with non-negative weights.
- **A***: When pathfinding with a heuristic is feasible (e.g., maps).
- **Floyd-Warshall**: When all-pairs shortest paths are required, especially for dense graphs.

Where |X| is the number of/size of (the double | are a visual glitch)
## Master Theorem
You can guesstimate the time complexity of an algorithm by its form. Use base case.
Note, ONLY WORKS IF:
1. monotonically increasing
2. has to be a polynomial
3. a cannot be a constant < 1

With a time complexity form of $T(n)=aT(\frac{n}{b})+n^d$
Where a is any number, b is the fraction number, and d is the HIGHEST EXPONENT
	For example, $T(n)=2\frac{T(n)}{4}+\sqrt{n}$. a = 2, b = 4, d = 1/2

| General Complexity    | Condition |
| --------------------- | --------- |
| $\Theta(n^d)$         | $a<b^d$   |
| $\Theta(n^d\log{n})$  | $a=b^d$   |
| $\Theta(n^{\log_ba})$ | $a>b^d$   |
## Big-O Notation
Big-$O$ is the growth rate for the UPPER BOUND. Worst case scenario basically
Big-$\Omega$ is the growth rate for the LOWER BOUND. Best case time complexity
Big-$\Theta$ is the growth rate for BOTH BOUNDS. It is only possible when the worst and best case scenario have the same growth order

These are usually used in comparison for equations. For example, $10n^3+n^2+1000$ has a Big-All three of n^3

NOTE THAT BIG-O IS SILLY AND CAN HAVE MULTIPLE CORRECT ANSWERS. For the same equation above, n^4 is also a valid answer as long as it's bigger than the Theta
## Design Strategies
Basically just what category of algorithm it is

- Divide-and-conquer -> divide the problem into subproblems and solve those then combine the answer
- Decrease-and-conquer -> same thing as divide but you decrease the size of the problem at each step (usually by magnitudes like logarithmically, constant, fraction)
- Greedy -> optimizes the final solution by picking the best/most optimal option at each step
- Memoization -> storing the results of constant function calls and reusing them instead of recalculating in every iteration (think Floyd-Warshall table)
- Brute-force exhaustion -> no strategy, try everything

## AVL Trees
This is going to just be the general Tree Section:tm: since I do not know if we need to know more than just AVL trees or not

Trees discussed: Minimum spanning trees, binary search trees, avl trees, red-black trees, 2-3 trees
Binary heap is getting it's own section so it's not here

| **Data Structure**           | **What It Is**                                                                                                           | **Constraints**                                                                                                                                                                                                                                             | **Operations (Time Complexity)**                                                                                                                                                                                                                                | **Use Cases**                                                                                                                     | **Other Notes**                                                                                                                                                                                                                                            |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Minimum Spanning Tree**    | A tree that connects all vertices in a graph with the minimum total edge weight.                                         | 1. No cycles: Must form a tree (acyclic). <br>2. Must span all the vertices of the graph.  <br>3. Total edge weight must be minimized.  <br>4. For edge weights: if all weights are unique, the MST is unique; otherwise, there may be multiple valid MSTs. | - **Building Prim's and Kruskal's**:<br>If priority queue is an unordered array and graph is weight matrix<br>$O(\vert V\vert^2)$<br><br>If pq is min-heap and graph is adjacency lists<br>$O(\vert E\vert\cdot \log \vert V\vert)$<br>- **Query/Find**: $O(1)$ | Routing networks traffic                                                                                                          | Prim’s: better for dense graphs because it focuses on vertices<br>Kruskal’s: better for sparse graphs and easier to implement                                                                                                                              |
| **Binary Search Tree (BST)** | A binary tree where the left child ≤ root < right child.                                                                 | 1. A node can have 0-2 children<br>2. Left child <= root <= right child                                                                                                                                                                                     | - **Search**: $O(\log n)$<br>- **Insert**: $O(\log n)$<br>- **Delete**: $O(\log n)$<br>(basically the height, worst-case $O(n)$)                                                                                                                                | - Lookup, insert, and delete operations where data is dynamic and sorted.  <br>- In-order traversal for sorted order of elements. | Simple but can degrade to O(n) height for skewed trees. No self-balancing.<br><br>TRAVERSAL METHODS:<br>Pre-order: visit self, left child, right child<br>In-order: visit left child, self, right child<br>Post-order: visit left child, right child, self |
| **AVL Tree**                 | A self-balancing binary search tree where the height difference (balance factor) between child nodes is at most 1.       | 1. A node can have 0-2 children<br>2. Left child <= root <= right child<br>3. The difference in height between the right subtree and the left subtree can be at most 1                                                                                      | - **Search**: $O(\log n)$<br>- **Insert**: $O(\log n)$<br>- **Delete**: $O(\log n)$<br>- **Rebalancing:** $O(\log n)$<br>- **Rotations:** $O(1)$                                                                                                                | - Databases where frequent updates and lookups occur.  <br>- Use cases needing strict balance guarantees for efficient lookups.   | Height is within a rough constant factor of $log_2n$ or 1.5x, so the general form for operations is O(log(n))                                                                                                                                              |
| **Red-Black Tree**           | A self-balancing binary search tree where nodes are red or black, and balancing ensures properties such as black height. | 1. 0-2 children per node<br>2. Every node is either red or black. Root is always black. Null nodes count as black<br>3. No two consecutive red nodes, new nodes are always red<br>4. Each subtree has the same number of black nodes                        | - **Search**: $O(\log n)$<br>- **Insert**: $O(\log n)$<br>- **Delete**: $O(\log n)$<br>- **Rebalancing:** $O(1)$<br>-**Rotation/Repainting**: $O(1)$                                                                                                            | - Scenarios where insertions and deletions are frequent but strict balancing isn't required.                                      | Does less rotations than an AVL tree by repainting.<br><br>Repainting:<br>If a constraint is violated, check the problem node's<br>- If aunt/uncle is black, rotate<br>- If aunt/uncle is red, flip colors of parent, aunt/uncle, and grandparent          |
| **2-3 Tree**                 | A balanced tree where every node has either 2 children (1 key) or 3 children (2 keys).                                   | 1. Every node has ONE data key and can have 0 or 2 children<br>2. Every node has TWO data key and can have 0 or 3 children<br>3. All leaves must be on the same level<br>4. Insert is always at a leaf except for root                                      | - **Search:** $\le O(\log n)$<br>- **Rebalancing:** $O(1)$<br><br>- Operations: Somewhere between $\log_3n$ and $\log_2n$<br><br>Rebalancing is $O(1)$ on average                                                                                               | - Scenarios requiring balanced trees but with fewer rotations compared to AVL.                                                    | Easier to think of as<br>case 1: 1 node with children that have 2 values<br>case 2: 1 node with 2 values and 3 children with 1 value                                                                                                                       |


![[Pasted image 20241212192505.png]]

![[Pasted image 20241212192938.png]]

## Heaps
Binary heaps:
- Binary heaps are one type of binary tree
- They must be complete
- Node data must obey the heap property that there can be 0-2 children

There are two types:
- Min-heap: parent data always ≤ children data
- Max-heap: parent data always ≥ children data

Because they need to be complete, they are often implemented with an array

When inserting/deleting, bubble values up/down as needed to correct issues

Time complexities:
- **Insert**: $O(\log n)$
- **Extract Min/Max (pop)**: $O(\log n)$
- **Peek (find min/max)**: $O(1)$
- **Heapify (build heap)**: $O(n)$
- **Decrease Key (or increase key)**: $O(\log n)$
- **Delete**: $O(\log n)$

Heap sort is $O(n\log n)$ and is NOT a stable algorithm

At worst, the most swaps needed after an insert would be $\log n −1$
## Loop Invariants
Pre/post conditions basically
Inline assert statements
Super easy

## Permutations and Combinations
Full permutation of all possible options: $$n!$$
Sub-permutation for size k: $$P_{n,k}=\frac{n!}{(n-k)!}$$

A <mark style="background: #ADCCFFA6;">combination</mark> is a possible set of objects chosen in any order; the order of selection does not matter. The formula for the number of ways to select unordered sets of size k from a collection of n objects is:
$$C_{n,k}=\frac{n!}{k!(n-k)!}$$
Read as n choose k. Also follows the format $C\left( \begin{array}{c} n \\ k \end{array} \right)$

