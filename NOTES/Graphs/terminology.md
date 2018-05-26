# Terminology

A graph {% math %}\Gamma{% endmath %} is a set {% math %}V{% endmath %} of **vertices** and a collection {% math %}E{% endmath %} of pairs of **vertices** from {% math %}V{% endmath %}, which are called **edges**. Vertices are sometimes called nodes or points, and edges are sometimes called arcs or lines.

Edges in a graph are either **directed** or **undirected**. An edge {% math %}(i, v){% endmath %} is said to be **directed** from {% math %}u{% endmath %} to {% math %}v{% endmath %} if the pair {% math %}(u, v){% endmath %} is ordered, else it is said to be **undirected**.

We say that a graph is **undirected** if all the edges in the graph are undirected. Likewise, a **directed graph** (also called a **digraph**), is a graph whose edges are all directed. A graph that has both directed and undirected edges is often called a **mixed graph**.

Two nodes joined by an edge are called **adjacent** (or **linked**).  The end vertices of an edge is known as the **endpoints** of that edge. If an edge is directed, its first endpoint is its **source** vertex and the other is the **target** vertex. A edge is said to be **incident** on a vertex if the vertex is one of the edges endpoints.

The **degree** of a vertex {% math %}v{% endmath %} is the number of incident edges of {% math %}v{% endmath %}. The **in-degree** and **out-degree** of a vertex {% math %}v{% endmath %} is the number of incoming and outgoing edges of {% math %}v{% endmath %}.

A graph is **sparse** if {% math %}E = O(N){% endmath %}, and **dense** of {% math %}E = O(N^2){% endmath %}, where {% math %}E{% endmath %} is the number of edges and {% math %}N{% endmath %} is the number of vertices.

### Paths
A **path** is a sequence of adjacent vertices and edges that start at a vertex and ends at a vertex, such that each edge is incident to its predecessor and successor vertex. A **cycle** is a path with the same start and end vertices. If there exists a path going from {% math %}A{% endmath %} to {% math %}B{% endmath %}, then we say {% math %}B{% endmath %} is **reachable** from {% math %}A{% endmath %}, or that {% math %}A{% endmath %} and {% math %}B{% endmath %} are **connected**. We say that a graph is **connected** if all pairs of nodes are connected.

A **cycle** is a path with the same start and end vertices. A **loop** is an edge from a vertex to itself.

#### Subgraphs
A **subgraph** of a graph {% math %}\Gamma{% endmath %} is a graph {% math %}\Gamma'{% endmath %} whose vertices and edges are subsets of the vertices and edges of {% math %}\Gamma{% endmath %}, respectively.

A **connected component** of a graph {% math %}\Gamma{% endmath %}, is the largest connected subgraph of {% math %}\Gamma{% endmath %}.