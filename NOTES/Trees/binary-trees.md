# Binary Trees

A **binary tree** is an ordered tree in which each node has at most two children. A binary tree is **proper** if each internal node has two children. For each internal node, its children are labelled as a **left child** and a **right child**. The children are ordered so that a left child comes **before** a right child.

A **proper binary tree** is an ordered tree in which each internal node has **exactly** two children.

## Abstract Data Type

As an abstract data type, a binary tree supports 3 additional accessor methods.

| Method Name | Description |
| ----------- | ----------- |
| `leftChild(v)` | returns the left child of *v* |
| `rightChild(v)` | returns the right child of *v* |
| `sibling(v)` | returns the sibling of *v* |

## Nodes in a binary tree
- At level {% math %} d {% endmath %}, where each node on this level has depth {% math %} d {% endmath %}, there is at most {% math %} 2^d {% endmath %} nodes.
- In a proper binary tree, the number of external nodes is one more than the number of internal nodes.

## Preorder traversal
```
Algorithm binaryPreorder(T, v)
  perform the action on the node v
  if v is an internal node then
    call binaryPreorder(T, T.leftChild(v))
    call binaryPreorder(T, T.rightChild(v))
```

## Postorder traversal
```
Algorithm binaryPreorder(T, v)
  if v is an internal node then
    call binaryPreorder(T, T.leftChild(v))
    call binaryPreorder(T, T.rightChild(v))
  perform the action on the node v
```

## Inorder traversal
In a inorder traversal, the action on a node *v* is performed in between the recursive traversals of its left and right subtrees. This can be viewed as visiting the nodes from left to right.
```
Algorithm binaryPreorder(T, v)
  if v is an internal node then
    call binaryPreorder(T, T.leftChild(v))
  perform the action on the node v
  if v is an internal node then
    call binaryPreorder(T, T.rightChild(v))

```