# Collision Handling

A collision occurs when for two distinct keys {% math %} k_1, k_2 {% endmath %} we have {% math %} h(k_1) = h(k_2) {% endmath %} - which prevents simple insertion of a new item {% math %} (k, e) {% endmath %} into a bucket {% math %} A[h(k)] {% endmath %}.

## Load Factors and Rehashing
If a good hashing function is used for storing {% math %} n {% endmath %} items of a dictionary in a bucket of size {% math %} N {% endmath %}, we expect each bucket to be of size {% math %} \sim n/N {% endmath %}. This parameter is known as the **load factor** and should be kept small. If this requirement is met, the running time of methods `findElement`, `insertItem` and `removeElement` is {% math %} O(n/N) {% endmath %}.

In order to keep the load factor below a constant, the size of the bucket array needs to be increased and also changes to the compression map must be made. Then we need to re-insert all the existing hash table elements into the new bucket array using the new compression map. This process is known as **rehashing**.

#### Separate Chaining
Separate chaining is a simple way of dealing with collisions is to make each bucket capable of storing more than one item. This requires each bucket {% math %} A[i] {% endmath %} to be implemented as a sequence, list or vector. Each bucket can be implemented as a miniature dictionary.

#### Open Addressing
Instead of allowing buckets to store multiple items, in open addressing, we only store one element per bucket - this is a more sophisticated approach with dealing with collisions.

## Linear Probing
In linear probing, if we attempt to insert an item {% math %} (k, e) {% endmath %} into a bucket {% math %} A[h(k)] = A[i] {% endmath %} that is already occupied, we try to insert an element in the positions {% math %} A[(i + j) \; \text{mod} \;N] {% endmath %} for {% math %} j = 1, 2, \cdots {% endmath %} until a free place is found. This approach requires `findElement(k)` to be implemented such that is examines consecutive buckets starting with {% math %} A[h(k)] {% endmath %}, until we either find the element or an empty bucket. `removeElement(k)` is more difficult to implement - one way would be to introduce a *deactivated item* object. With this object, `findElement(k)` and `removeElement(k)` should be implemented so that they skip over deactivated items and continue probing until a desired item or an empty bucket is found.

In conclusion, linear probing saves space, but complicates removals. It also clusters dictionaries into continuous runs, which slows down searches.

## Quadratic Probing
In quadratic probing, our iterative attempts are to buckets {% math %} A[(i + j^2) \; \text{mod} \;N] {% endmath %} for {% math %} j = 1, 2, \cdots {% endmath %} until an empty bucket is found. It complicates the removal operation, but avoids the clustering patterns characteristics with linear probing. However, it creates **secondary clustering** with a set of secondary cells bouncing around a hash table in a fixed pattern. If {% math %} N {% endmath %} is not a prime number, quadratic probing may fail to find an empty bucket, even if one exists. If the bucket array is over 50% full, this may happen even if {% math %} N {% endmath %} is prime.

## Double Hashing
Double hashing elimates data clustering produced by linear and quadratic probing. In double hashing, a secondary hash function {% math %} h' {% endmath %} is used. If the primary function {% math %} h {% endmath %} maps a key {% math %} k {% endmath %} to a bucket {% math %} A[h(k)] {% endmath %} that is already occupied, the following buckets are attempted iteratively: {% math %} A[(i + j \cdot h'(k)) \; \text{mod} \;N] {% endmath %} for {% math %} j = 1, 2, \cdots {% endmath %}. The second hash function must be non-zero. For a prime number {% math %} N {% endmath %}, the common choice is {% math %} h'(k) = q - (k \; \text{mod} \; q) {% endmath %}, where {% math %} q < N {% endmath %} is a prime number.

If memory size is not an issue, separate chaining is always competitive to collision handling schemes based on open addressing.