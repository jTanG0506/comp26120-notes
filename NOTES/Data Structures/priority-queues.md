# Priority Queues

A **priority queue** {% math %} P {% endmath %} is a container of elements with keys associated with them at the time of insertion, with two fundamental methods:
- `insertItem(k, e)` - inserts an element `e` with a key `k` into {% math %} P {% endmath %}
- `removeMin()` - returns and removes from {% math %} P {% endmath %} an element with the smallest key

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