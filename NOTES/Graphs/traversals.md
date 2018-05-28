# Traversals

A **traversal** of a tree or graph is a systematic procedure for exploring a tree or graph by examining all of its vertices and edges. For example, a *web crawler*, must explore a graph of hypertext documents by examining its vertices, which are the documents, and its edges, which are the hyperlinks between documents.

## Depth-First Search (DFS)
Depth-first search in an undirected graph G applies the backtracking technique and is analogous to wandering in a labyrinth with a string and a can of paint without getting lost. Here is a pseudocode description of recurive DFS. **Discovery edges** are edges used to discover new vertices, while **back edges** are those that lead to already explored vertices.

```
Algorithm DFS(G, v)
  Input: A graph G and a vertex v in G
  Output: The vertices in the connected component of v (in explored)

  Label v as explored
  for each edge e that is incident to v in G do
    if e is unexplored then
      Let w be the end vertex of e opposite from v
      if w is unexplored then
        label e as a dicovery edge
        DFS(G, w)
      else
        Label e as a back edge
      end
    end
  end
```

## Breadth-First Search (BFS)
Breadth-first search traverses a connected component of a graph, and in so doing, defines a useful spanning tree. BFS proceeds in rounds and subdivides the vertices into *level*, which represent the minimum number of edges from the start vertex to each vertex. The start idex is given level 0, and acts as an anchor. In the first round, we explore all the vertices we can reach in one edge, marking each as explored, and placing these vertices into level 1. In the second round, we explore all the vertices that can be reached in two edges from the start vertex. These new vertices, which are adjacent to level 1 vertices and not previous assigned to a label, are placed into level 2, and so on.

```
Algorithm BFS(G, s)
  Input: A graph G and a vertex s of G
  Output: A labeling of the edges in the connected component of s as discovery and cross edges

  Create an empty list L(0)
  Mark s as explored and insert s into L(0)
  i <- 0
  while L(i) is not empty do
    create an empty list L(i + 1)
    for each vertex v in L(i) do
      for each edge e = (v, w) incident on v in G do
        if edge e is unexplored then
          if vertex w is unexplored then
            Label e as a discovery edge
            Mark w as explored and insert w into L(i + 1)
          else
            Label e as a cross edge

    i <- i + 1
  end
```

#### Complexity of DFS and BFS
- For the **adjacency list** representation, the complexity is linear, {% math %}O(N + E){% endmath %}

- For the **adjacency matrix** representation, the complexity is quadratic, {% math %}O(N^2){% endmath %}

## Priority Search
Priority searches are often used to implement **heuristic search methods** where the priority is calculated at each node to provide an indication of whether a route through this node is likely to reach a required goal. In a priority search, we visit the root, then at each step, visit a node that has the **highest priority** amongst univisted children of visited nodes.

## Generic Search
All the above search techniques (traversals) can be coded with the same program. The program uses an axuiliary data structure with operations `push`, `pop`, `top` and `empty`. A **priority queue** has the operations of a queue, but `top` returns **an item of highest priority in the queue** and `pop` removes this item.

- When the data structure is a **stack**, the traversal is **DFS**

- When the data structure is a **queue**, the traversal is **BFS**

- When the data structure is a **priority queue**, the traversal is **priority search**

The idea is to start by pushing the root node of the tree onto the structure, then visit the top element of the structure, pop it and push its children onto the structure. Therefore the structure stores the unvisited children of visited nodes, in the order which they are encountered.

## Graph Traversals
A tree is a directed graph such that there is a distinguished node (the root) such that there is a unique path from the root to any node in the graph. To modify tree traversal for graphs, we may revisit nodes - so mark nodes as viisted/unvisited and only continue traversal from unvisited nodes, and there may not be one node from which all others are reachable - so choose a node, perform traversal, then start traversal again from any unvisited nodes.