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