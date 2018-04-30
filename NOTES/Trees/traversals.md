# Traversal of a tree

A **traversal** of a tree {% math %} T {% endmath %} is a systematic way of accessing all the nodes of {% math %} T {% endmath %}. There are two different traversal schemes for trees, **preorder** and **postorder**.

### Preorder Traversal
In a preorder traversal of a tree {% math %} T {% endmath %}, the root is visited first, then the subtrees rooted at its children are traversed recursively. The overall running time of the preorder traversal is {% math %} O(n) {% endmath %}. In preorder traversal, the action is performed on the parents before their children.

```
Algorithm preorder(T, v)
  perform the action on the node v
  for each child w of v do
    preorder(T, w)
```

### Postorder Traversal
A postorder traversal is essentially the complement of a preorder traversal. It traverses recursively the subtrees rooted at the children of the root first, before visiting the root. In postorder traversal, the action is performed on the children before its parent - which is useful for certain computed properties. Postorder traversal also has overall runtime of {% math %} O(n) {% endmath %}.

```
Algorithm postorder(T, v)
  for each child w of v do
    postorder(T, v)
  perform the action on the node v
```