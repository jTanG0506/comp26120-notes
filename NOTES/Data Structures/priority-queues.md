# Priority Queues

A **priority queue** *P* is a container of elements with keys associated with them at the time of insertion, with two fundamental methods:
- `insertItem(k, e)` - inserts an element `e` with a key `k` into *P*
- `removeMin()` - returns and removes from *P* an element with the smallest key

## Comparators

A **comparator** is an object that compares two keys and is associated with a priority queue at the time of construction.

| Method Name | Description |
| ----------- | ----------- |
| `isLess(a, b)` | returns `true` if {% math %} a < b {% endmath %} |
| `isLessOrEqualTo(a, b)` | returns `true` if {% math %} a \leq b {% endmath %} |
| `isEqualTo(a, b)` | returns `true` if {% math %} a = b {% endmath %} |
| `isGreater(a, b)` | returns `true` if {% math %} a > b {% endmath %} |
| `isGreaterOrEqualTo(a, b)` | returns `true` if {% math %} a \geq b {% endmath %} |
| `isComparable(a)` | returns `true` if {% math %} a {% endmath %} can be compared |