# Vector based representation

A vector-based structure for representing **binary** trees is based on a simple way of numbering the nodes of {% math %} T {% endmath %}. We define a numbering function {% math %} p(.) {% endmath %}, which is known as a **level numbering** of the nodes in a binary tree {% math %} T {% endmath %}.

{% math %}
p(v) = \left\{
        \begin{array}{ll}
            1 & \quad \text{if} \, v \, \text{is the root} \\
            2p(u) & \quad \text{if} \, v \, \text{is the left child of the node} \, u \\
            2p(u) + 1 & \quad \text{if} \, v \, \text{is the right child of the node} \, u
        \end{array}
    \right.
{% endmath %}

![Vector Tree](assets/vector-tree-wide.png)

## Running times
| Operation | Complexity |
| --------- | ---------- |
| `positions()`, `elements()` | {% math %} O(n) {% endmath %} |
| `swapElement(v, w)`, `replaceElements(v, e)` | {% math %} O(1) {% endmath %} |
| `root()`, `parent(v)`, `children(v)` | {% math %} O(1) {% endmath %} |
| `leftChild(v)`, `rightChild(v)`, `sibling(v)` | {% math %} O(1) {% endmath %} |
| `isInternal(v)`, `isExternal(v)`, `isRoot(v)` | {% math %} O(1) {% endmath %} |