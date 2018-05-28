# Binary Search Trees

## Binary Search
If {% math %} S {% endmath %} is an ordered sequence of {% math %} n {% endmath %} elements, then the element at rank (position) {% math %} i {% endmath %} has a key that is not smaller than the keys of the items at ranks {% math %} 0, \cdots, i - 1 {% endmath %} and no larger than the keys of items at ranks {% math %} i + 1, \cdots, n - 1 {% endmath %}. This ordering allows quick searching of the sequence {% math %} S {% endmath %}. The algorithm has two parameters **high** and **low**. All candidates for a sought element at a current stage of the search are bracketed between these two parameters.

```
Algorithm BinarySearch(S, k, low, high)
  Input: An ordered vector S storing n items, a search key k and the (low, high) integer pair
  Output: An element of S with the key k, otherwise an exception

  if low > high then
    return NO_SUCH_KEY
  else
    mid = int((low + high) / 2)
    if k = key(mid) then
      return e(mid)
    elseif k < key(mid) then
      BinarySearch(S, k, low, mid - 1)
    else
      BinarySearch(S, k, mid + 1, high)
    end
  end
```

#### Computational Cost
First, notice that at each call of the algorithm there is a constant number of operations, thus the running time is proportional to the number of recursive calls. At each recursive call, the number of candidates that need to be considered is {% math %} high - low + 1 {% endmath %}, which is reduced by at least half at each recursive call. If {% math %} T(n) {% endmath %} is the computational cost of a binary search, then:
{% math %}
T(n) = \left\{
        \begin{array}{ll}
            c & \quad \text{if} \, n < 2 \\
            T(n / 2) + c & \quad \text{otherwise}
        \end{array}
    \right.
{% endmath %}
In the worse case, the stop terminates when there are no more candidate items, so the maximal number of recursive calls is {% math %} m {% endmath %} such that {% math %} n / 2^m < 1 {% endmath %}, which implies that {% math %} \lfloor \log n \rfloor + 1 {% endmath %}, so `BinarySearch(S, k, 0, n - 1)` runs in {% math %} O(\log n) {% endmath %} time.