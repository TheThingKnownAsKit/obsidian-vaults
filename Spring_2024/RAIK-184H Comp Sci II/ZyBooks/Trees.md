# INTRODUCTION TO TREES
A **tree** is an undirected graph that is connected and has no cycles. Think file system
A **free tree** has no particular organization of the vertices and edges. A **rooted tree** has a designated root that all vertices and edges sprout from
![[Pasted image 20240218140037.png]]

The **level** of a vertex is its distance from the root. The **height** is the highest level of any vertex (note: height starts at 0 from the vertex. right one has height 3)

Weird terminology that probably isn't important:
- Every vertex in a rooted tree T has a unique *parent*, except for the root which does not have a parent. The parent of vertex v is the first vertex after v encountered along the path from v to the root. 
- Every vertex along the path from v to the root (except for the vertex v itself) is an *ancestor* of vertex v. 
- If v is the parent of vertex u, then u is a *child* of vertex v. 
- If u is an ancestor of v, then v is a *descendant* of u. 
- A *leaf* is a vertex which has no children.
- Two vertices are *siblings* if they have the same parent. 
- A *subtree* rooted at vertex v is the tree consisting of v and all v's descendants. 

# PROPERTIES OF TREES
Theorems:
* There is a unique path between every pair of vertices in a tree
* Any free tree with at least two vertices has at least two leaves
* Let T be a tree with n vertices and m edges, then m = n - 1

Properties/Terms:
* A leaf of a free tree is a vertex of degree 1. A vertex is an **internal vertex** if the vertex has a degree at least two
* A **forest** is a graph that has no cycles and that is not necessarily connected

# TREE TRAVERSALS
Tree **traversal** involves systematically visiting every vertex to search for a specific system
![[Pasted image 20240218143605.png]]

In a **pre-order traversal**, a vertex is visited before its descendants. In a **post-order traversal** a vertex is visited after its descendants
![[Pasted image 20240218143811.png]]

Note: both work left to right

# SPANNING TREES AND GRAPH TRAVERSALS
A **spanning tree** of a connected graph G is a subgraph of G which contains all the vertices in G and is a tree.
![[Pasted image 20240218164125.png]]
All dots need to be connected. Doesn't matter how, they just need to be connected somehow

There are two common methods for finding spanning trees in a graph: **Breadth-First** Search and **Depth-First** Search. Both methods start at a single vertex and incrementally build a connected tree by adding edges and vertices. The resulting tree is rooted at the start vertex. **Graph traversal** is a process that systematically explores all the vertices of a graph. Breadth-first search and depth-first search are used as a subroutine for traversing a graph in many other graph algorithms.
	Depth-First Search (DFS) favors going deep into the graph and tends to produce trees with longer paths from the start vertex. Note: alphabetical
	![[Pasted image 20240218165042.png]]
	Breadth-First Search (BFS) explores the graph by distance from the initial vertex, starting with its neighbors and expanding the tree to neighbors of neighbors, etc
	![[Pasted image 20240218165806.png]]
	![[Pasted image 20240218165819.png]]

# MINIMUM SPANNING TREE
A **weighted graph** is a graph G = (V ,E), along with a function w: E → R. The function w assigns a real number to every edge.
![[Pasted image 20240218171113.png]]
![[Pasted image 20240218171126.png]]

A **minimum spanning tree (MST)** of a weighted graph, is a spanning tree T of G whose weight is no larger than any other spanning tree of G.

**Prim's algorithm** finds a minimum spanning tree of the input weighted graph.
![[Pasted image 20240218171321.png]]
