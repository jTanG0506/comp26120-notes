# Heaps

A **heap** is a data structure which resembles the [binary tree data structure](../Trees/binary-trees.md) and provides a efficient way to implement a **priority queue**, with both insertions and removals in logarithmic time.

We will assume a total order relationship on the keys and will discuss **minheaps** in this section, which means elements with a lower value have a higher priority. The details for **maxheap** is analogous.

The keys for the internal nodes of the heaps must satisify two additional properties:
- a relational property (which affects how the keys are stored)
- a structural property

### Heap Order Property
In a heap {% math %} T {% endmath %}, for every node {% math %} v {% endmath %} other than the root, the key stored in {% math %} v {% endmath %} is greater or equal than the key stored at its parent.

The consequence is that the keys encountered on a path from the root to an external node are in a non-decreasing order and that a minimum key is always stored at the root.

### Complete Binary Tree Property
A binary tree *T* with height {% math %} h {% endmath %} is complete if the levels {% math %} 0 {% endmath %} to {% math %} h - 1 {% endmath %} have the maximum number of nodes and in the level {% math %} h - 1 {% endmath %}, all internal nodes are to the left of external nodes.

## Implementing a PQ using a Heap
A heap-based priority queue consists of:
- **heap**: a complete binary tree (implemented as a vector) with keys that satisfy the heap-order property
- **last**: a reference to the last node in {% math %} T {% endmath %}. For a vector implementation, last is an integer index to the vector element storying the last node of {% math %} T {% endmath %}
- **comp**: a comparator that defines total order relation among the keys, which should also maintain the minimal element at the root

#### Complexity
- A heap {% math %} T {% endmath %} with {% math %} n {% endmath %} has height {% math %} h = \lceil\log(n + 1)\rceil {% endmath %}
- Update operations are performed in time proportional to its height, rather than the number of its elements, hence these operations will have complexity {% math %} O(\log n) {% endmath %}