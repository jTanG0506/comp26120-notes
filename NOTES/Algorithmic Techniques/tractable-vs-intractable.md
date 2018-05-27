# Tractable vs Intractable Problems

An algorithm is said to be **polynomial-time** if its worse case time complexity is amongst {% math %}O(1), O(N), O(N^2), O(N^3), ...{% endmath %}. We consider these as *fast algorithms* and as **tractable solutions** to a problem.

Algorithms that behave in the worst-case as {% math %}2^N, N^N{% endmath %} or {% math %}N!{% endmath %} are very slow and are considered as **intractable algorithms** in general.

## Exponential Algorithms
Exponential algorithms arise from various algorithmic techniques, such as exhaustive enumeration (listing all possibilities and checking each for the solution requirement) and systematic searching of the space of partial solutions using unbounded backtracking.

## Graph Colouring Problem
A **colouring of a graph with k colours** is an allocation of the colours to the nodes of the graphs, such that each node has just one colour and nodes linked by an edge have different colours. The minimum number of colours required to colour a graph is its **chromatic number**.

#### Enumeration
Exhaustive enumeration is the simplest approach to colouring a graph of {% math %} k {% endmath %} colours:
- **enumerate** all allocations of {% math %} k {% endmath %} colours to the nodes of the graph
- **check** each allocation to see if it is a valid colouring

For a graph with {% math %} N {% endmath %} nodes and {% math %} E {% endmath %} edges, there are {% math %} k^N {% endmath %} allocations of {% math %} k {% endmath %} colours to the nodes. Checking each allocation to see if it is a valid colouring, is {% math %} O(E) {% endmath %}, so this algorithm has worse-case time complexity {% math %} O(E \times k^N) {% endmath %}.

#### Systematic Search
Number the nodes {% math %} 1, \cdots, N {% endmath %}. For each node encountered, successively try each colour in turn. If all fails, undo the colour allocation of the previous node and try a new colour. If it succeeds, then try colouring the next node. This algorithm is exponential in worst-case.

```
n = 1
while n <= N do
  attempt to colour node n with next colour not tried for n
  if there is no such colour then
    if n > 1 then
      n = n - 1
    else
      fail
  else if n = N then
    print colouring
  else
    n = n + 1
```

#### Conclusion
In fact, all known algorithms for graph colouring for {% math %} k \geq 3 {% endmath %} are exponential. This is an example of an **NP-complete problem**, where known solutions are exponential. Whether NP-complete problems admit polynomial-time algorithms is one of the most important open problems in Computer Science.