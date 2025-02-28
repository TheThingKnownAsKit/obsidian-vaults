# INTRODUCTION TO GRAPHS
An **undirected graph** is when the edges are unordered pairs of vertices
	which is useful for modeling relationships that are symmetric
	A graph is **finite** if the vertex set is finite
	A single element of V is called a **vertex** usually represented by a dot
![[Pasted image 20240225143933.png]]
TERMINOLOGY:
- If there is an edge between two vertices, they are said to be **adjacent**.
	- In the graph above, d and e are adjacent, but d and b are not adjacent.
- Vertices b and e are the **endpoints** of edge {b, e}. The edge {b, e} is **incident** to vertices b and e.
- A vertex c is a **neighbor** of vertex b if and only if {b, c} is an edge.
	- In the graph above, the neighbors of b are the vertices a, c, and e.
- In a simple graph, the **degree** of a vertex is the number of neighbors it has.
	- In the graph above, the degree of b is 3 and the degree of vertex a is 2. The degree of vertex b is denoted by deg(b).
- The **total degree** of a graph is the sum of the degrees of all of the vertices.
	- The total degree of the graph above is 2 + 3 + 3 + 2 + 2 = 12.
- In a **regular graph**, all the vertices have the same degree. In a **d-regular graph**, all the vertices have degree d.
	- The graph above is not regular because deg(a) ≠ deg(b). However the graph below is 3-regular.
- A graph $H = (V_{H}, E_{H})$ is a subgraph of a graph $G = (V_{G}, E_{G})$ if $V_{H}$ ⊆ $V_{G}$ and $E_{H}$ ⊆ $E_{G}$. Note that any graph G is a subgraph of itself. The diagram below shows a subgraph H of the graph G
	![[Pasted image 20240225144647.png]]

![[Pasted image 20240225143947.png]]

Graphs can be separated into multiple pieces or not connected at all
![[Pasted image 20240225144031.png]]

**Parallel edges** are multiple edges between the same pair of vertices
A graph can also have a **self-loop** which is an edge between a vertex and itself
	The graph below has two parallel edges between vertices a and b. There is also a self-loop at vertex c
	![[Pasted image 20240225144208.png]]

If a graph does not have parallel edges or self-loops, it is said to be a **simple graph**
	Unless otherwise specifies, assume graphs are simple in this class

The *number of edges and total degree can be calculated using the follow:*
Twice the number of edges is equal to the total degree (2 times edges = total degree)
$\sum_{v\epsilon V}deg(v)=2*|E|$

Common graphs in graph theory:
![[Pasted image 20240225145243.png]]
Positive integer n and m
- K$_n$ is called the **complete graph** on n vertices. K$_n$ has an edge between every pair of vertices. The figure shows K6. Kn is sometimes called a **clique** of size n or an n-clique.
- Cn is called a cycle on n vertices. The edges connect the vertices in a ring. The picture above depicts C7. Note that Cn is well defined only for n ≥ 3.
- The n-dimensional hypercube, denoted Qn, has 2n vertices. Each vertex is labeled with an n-bit string. Two vertices are connected by an edge if their corresponding labels differ by only one bit. For example in a 5-dimensional hypercube, the vertex labeled 11001 would have an edge to 11011 because the two strings only differ in the 4th location. The figure above shows a diagram of the 3-dimensional hypercube
- Kn,m has n+m vertices. The vertices are divided into two sets: one with m vertices and one set with n vertices. There are no edges between vertices in the same set, but there is an edge between every vertex in one set and every vertex in the other set. The figure shows a diagram of K3,4.

# GRAPH REPRESENTATIONS
Two graphs are the same graph if they have the same vertex and edge sets

In the **adjacency list representation** of a graph, each vertex has a list of all its neighbors
	Note, since undirected if vertex a is in b's list of neighbors, then b must also be in a's list of neighbors
	![[Pasted image 20240225150103.png]]

The **matrix representation** for a graph with n vertices is an n by n matrix whose entries are all either 0 or 1, indicating whether or not each edge is present. $M_{i,j}$ denotes the entry in row i column j
![[Pasted image 20240225150446.png]]

# GRAPH ISOMORPHISM
Two graphs are said to be **isomorphic** if there is a correspondence between vertex sets of each graph such that there is an edge between two vertices of one graph is and only if there is an edge between the corresponding vertices of the second graph
	The graphs are not identical but they can be relabeled so they are identical
![[Pasted image 20240225151114.png]]
![[Pasted image 20240225151130.png]]
![[Pasted image 20240225151143.png]]

If graph G is isomorphic to graph G', then G has a vertex of degree d if and only if G' has a vertex of degree d. A property is said to be **preserved under isomorphism** if whenever two graphs are isomorphic, one graph has the property if and only if the other graph also has the property.
![[Pasted image 20240225151306.png]]

The **degree sequence** of a graph is a list of the degrees of all of the vertices in non-increasing order. Non-increasing order means that each number is less than or equal to the preceding number in the sequence
	Consistent if preserved under isomorphism

Things NOT preserved under isomorphism:
- The lowest numbered vertex has degree 3
- Every even numbered vertex has odd degree
- Sum of the degrees of the even numbered vertices

# WALKS, TRAILS, CIRCUITS, PATHS, AND CYCLES
![[Pasted image 20240225152141.png]]

- A **trail** is a walk in which no edge occurs more than once.
- A **path** is a walk in which no vertex occurs more than once.
- A **circuit** is a closed trail.
- A **cycle** is a circuit of length at least 1 in which no vertex occurs more than once, except the first and last vertices which are the same.

# GRAPH CONNECTIVITY
- A set of vertices in a graph is said to be **connected** if every pair of vertices in the set is connected.
- A graph is said to be connected if every pair of vertices in the graph is connected, and is **disconnected** otherwise.

 A **connected component** consists of a maximal set of vertices that are connected as well as all the edges between any two vertices in the set.
	 The word "maximal" means that if any vertex is added to a connected component, then the set of vertices will no longer be connected

A vertex that is not connected with any other vertex is called an **isolated vertex** and is therefore a connected component with only one vertex.

An undirected graph G is **k-vertex-connected** if the graph contains at least k + 1 vertices and remains connected after any k - 1 vertices are removed from the graph. The **vertex connectivity** of a graph is the largest k such that the graph is k-vertex-connected. The vertex connectivity of a graph G is denoted κ(G).
	The vertex connectivity of a graph is the minimum number of vertices whose removal disconnects the graph into more than one connected component.
	When the graph is a complete graph, there is no set of vertices whose removal disconnects the graph. For the special case of Kn, the vertex connectivity κ(Kn) is just defined to be n - 1.

An undirected graph G is **k-edge-connected** if removing any k - 1 or fewer edges results in a connected graph. The **edge connectivity** of a graph is the largest k such that the graph is k-edge-connected. The edge connectivity of a graph G is denoted λ(G).
	The edge connectivity of a graph is the minimum number of edges whose removal disconnects the graph into more than one connected component.

![[Pasted image 20240225152747.png]]

# EULER CIRCUITS AND TRAILS
An **Euler circuit** in an undirected graph is a circuit that contains every edge and every vertex.
	Note that a circuit, by definition, has no repeated edges, so an Euler circuit contains each edge exactly once.
![[Pasted image 20240225153058.png]]

![[Pasted image 20240225153001.png]]
![[Pasted image 20240225153116.png]]
![[Pasted image 20240225153127.png]]

![[Pasted image 20240225153232.png]]![[Pasted image 20240225153320.png]]

An **Euler trail** is an open trail that includes each edge. Note that a trail, by definition, has no repeated edges, so an Euler trail contains each edge exactly once. In an open trail, the first and last vertices are not equal
![[Pasted image 20240225153509.png]]

# HAMILTONIAN CYCLES AND PATHS
A **Hamiltonian cycle** in an undirected graph is a cycle that includes every vertex in the graph. Note that a cycle, by definition, has no repeated vertices or edges, except for the vertex which is at the beginning and end of the cycle. Therefore, every vertex in the graph appears exactly once in a Hamiltonian cycle, except for the vertex which is at the beginning and end of the cycle

A **Hamiltonian path** in an undirected graph is a path that includes every vertex in the graph. Note that a path, by definition, has no repeated vertices or edges, so every vertex appears exactly once in a Hamiltonian path.

You can transform a cycle into a path by deleting the last vertex. If it has a cycle, it has a path
![[Pasted image 20240225153808.png]]