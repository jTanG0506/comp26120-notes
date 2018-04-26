# Abstract Data Type

The methods below are those that you would expect to find in a implementation of a tree data structure.

## Accessor Methods
| Method Name | Description | Complexity |
| ----------- | ----------- | ---------- |
| `root()` | returns the root of the tree | {% math %} O(1) {% endmath %} |
| `parent(v)` | returns the parent node of *v*, or `nil` if *v* is root | {% math %} O(1) {% endmath %} |
| `children(v)` | returns an iterator of the children of the node *v* | {% math %} O(c_v) {% endmath %}* |

\* where {% math %} c_v {% endmath %} is the number of children of *v*

## Query Methods
| Method Name | Description | Complexity |
| ----------- | ----------- | ---------- |
| `isInternal(v)` | tests whether the node *v* is internal | {% math %} O(1) {% endmath %} |
| `isExternal(v)` | tests whether the node *v* is external | {% math %} O(1) {% endmath %} |
| `isRoot(v)` | tests whether the node *v* is the root | {% math %} O(1) {% endmath %} |

## Generic Methods (not necessarily related to the tree structure)
| Method Name | Description | Complexity |
| ----------- | ----------- | ---------- |
| `size()` | returns the number of nodes of the tree | {% math %} O(1) {% endmath %} |
| `elements()` | returns an iterator of all the elements stored at the nodes of the tree | {% math %} O(n) {% endmath %} |
| `positions()` | returns an iterator of all the nodes of the tree | {% math %} O(n) {% endmath %} |
| `swapElements(v, w)` | swaps the elements stored at the nodes *v* and *w* | {% math %} O(1) {% endmath %} |
| `replaceElement(v, e)` | returns the element *v* and replaces it with the element *e* | {% math %} O(1) {% endmath %} |