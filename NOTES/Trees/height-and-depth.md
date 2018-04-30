# Height and Depth

### Depth of a node
Let *v* be a node of a tree {% math %} T {% endmath %}. The **depth** of {% math %} v {% endmath %} is the number of ancestors of {% math %} v {% endmath %}, excluding {% math %} v {% endmath %} itself. The depth of the root is 0.

```
Algorithm depth(T, v)
  if T.isRoot(v) then
    return 0
  else
    return 1 + depth(T, T.parent(v))
```

![Depth of a node](assets/depth-wide.png)

### Height of a tree
The **height** of a tree is equal to the maximum depth of an external node of {% math %} T {% endmath %}.

```
Algorithm height(T, v)
  if T.isExternal(v) then
    return 0
  else
    h = 0
    for each w in T.children(v) do
      h = max(h, height(T, w))
    return 1 + h
```

![Height of a tree](assets/height-wide.png)