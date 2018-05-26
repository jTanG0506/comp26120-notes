# Representation

Two of the common data structures to represent graphs are the **adjacency list** and the **adjacency matrix**.

## Adjacency List
The **adjacency list** structure representation for a graph {% math %}\Gamma{% endmath %} consists of a list of all vertices and with each vertex {% math %}v{% endmath %}, a list of all the edges incident on {% math %}v{% endmath %}. For a vertex {% math %}v{% endmath %}, the space used by the adjacency list for {% math %}v{% endmath %} is proportional to the degree of {% math %}v{% endmath %}, so {% math %}O(\text{deg}(v)){% endmath %}. It follows that the space requirement of the adjacency list structure for a graph {% math %}\Gamma{% endmath %}, with {% math %}n{% endmath %} vertices and {% math %}m{% endmath %} edges, is {% math %}O(n + m){% endmath %}.

## Adjacency Matrix
An **adjacency matrix** structure representation for a graph {% math %}\Gamma{% endmath %} consists of a two-dimensional matrix, {% math %}A{% endmath %}, where each dimension indexed by the vertices of the graph. We number the vertices {% math %}0, 1, \cdots, n{% endmath %} and we view the edges as being pairs of such integers.

The entries in the adjacency matrix are defined as followed:
{% math %}
\large
A[i, j] =
\begin{cases} 
  1 & \text{if} \; (i, j) \; \text{is an edge in} \; \Gamma \\
  0 & \text{otherwise}
\end{cases}
{% endmath %}

By using adjacency matrix {% math %}A{% endmath %}, we can determine whether two vertices, {% math %}u{% endmath %} and {% math %}v{% endmath %} are adjacent, in {% math %}O(1){% endmath %}. The trade-off for an adjacency matrix is that it requires {% math %}O(n^2){% endmath %} space, where {% math %}n{% endmath %} is number of vertices. Also, to find all the nodes that are adjacent to a given node, we now have to look through an entire row, which takes {% math %}O(n){% endmath %} time.

#### Which one to use?
Choosing between an adjacency list and an adjacency matrix usually boils town to determining how **dense** the graph {% math %}\Gamma{% endmath %} is. For example, if {% math %}\Gamma{% endmath %} has close to a quadratic number of edges, then the adjacency matrix is often a good choice for representing {% math %}\Gamma{% endmath %}. However, if {% math %}\Gamma{% endmath %} has close to a linear number of edges, then the adjacency list representation is probably superior.

These representations will need modification in order to support various data types. For **edge-weighted graphs**, we will need to include the weights in the representation. For **multigraphs**, we may record the edges as well as the adjacent nodes in a list representation, or the number of edges in a matrix representation.

#### Example
> Consider the task of finding whether there is a path of length 2 from a given node S to another node T.

With the adjacency list structure, we consider the list of nodes adjacent to {% math %}S{% endmath %}, which in worse case, is the {% math %}E{% endmath %}, the number of edges in graph. For each node in this list, we check to see whether {% math %}T{% endmath %} is in its list. Thus the worse case time complexity is {% math %}O(E^2){% endmath %}.

If we multiply an adjacency matrix by itself, we get a resulting matrix which tells which nodes are connected by a path of length 2. Since we are only interested of a length 2 path between {% math %} S {% endmath %} and {% math %} T {% endmath %}, we only one entry in said matrix. To calculate the entry, we do {% math %} N {% endmath %} multiplications, so it is {% math %} O(N) {% endmath %}.