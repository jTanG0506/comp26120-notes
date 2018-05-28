# Survey of Graph Algorithms

Many graph algorithms are based on the traversals: DFS, BFS and Priority Search.

## DFS based algorithms
- finding the connected components of a graph
- detecting cycles in a graph
- finding *strong components* of a graph
- planarity testing and embedding
- articulation points and blocks of undirected graphs (orientability and reducibility)

## Path finding problems
- to find all paths between all nodes (transitive closure)
- to find all paths between a fixed pair of nodes
- to find all paths from one node to all others (single source problem)

If the edges are labelled with numerical values, then we can ask for the *shortest paths*, by which we mean a path of minimum length, where the length of a path is the sum of its edges labels - this is known as an **optimisation** problem.

#### Optimisation Property
There is an **optimisation property** concering shortest paths.
> If p is a shortest path from node u to node v via node w, then the portions of p from u to w and from w to v are both shortest paths.

Such optimisation properties means that there are direct methods of computing shortest paths: to accumulate shortest paths we need combine only other shortest paths and not consider any other paths - this is the basis for both **Floyd's algorithm** and **Dijkstra's algorithm**.

## Planarity
Planarity is about depicting graphs in 2D space - how to we draw graphs and can we do so without edges crossing?

An **embedding** of a (directed or undirected) graph in the plane is an allocation of distinct points in the plane to the nodes and distinct continuous lines to the edges, so that no two lines intersect. There may be more than one *way* of embedding a graph in the plane, but not all graphs can be embedded in the plane. Graphs which can be embedded in the plane is called a **planar** graph.

#### Graph Colour
A **colouring** of a graph with {% math %}k{% endmath %} colours is an allocation of the colours to the nodes of the graph, such that each node has just one colour and nodes linked by an edge have different colours. To determine whether a graph can be coloured with {% math %}k \geq 3{% endmath %} colours is an **NP-complete problem**. Thus the only algorithms that exist in general for colourability are exhaustive unlimited back-tracking algorithms, and hence are exponential-time.

> Proposition: every planar graph can be coloured with just 4 colours.