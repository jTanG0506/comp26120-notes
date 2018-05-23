# Collision Handling

A collision occurs when for two distinct keys {% math %} k_1, k_2 {% endmath %} we have {% math %} h(k_1) = h(k_2) {% endmath %} - which prevents simple insertion of a new item {% math %} (k, e) {% endmath %} into a bucket {% math %} A[h(k)] {% endmath %}.

## Load Factors and Rehashing
If a good hashing function is used for storing {% math %} n {% endmath %} items of a dictionary in a bucket of size {% math %} N {% endmath %}, we expect each bucket to be of size {% math %} \sim n/N {% endmath %}. This parameter is known as the **load factor** and should be kept small. If this requirement is met, the running time of methods `findElement`, `insertItem` and `removeElement` is {% math %} O(n/N) {% endmath %}.

In order to keep the load factor below a constant, the size of the bucket array needs to be increased and also changes to the compression map must be made. Then we need to re-insert all the existing hash table elements into the new bucket array using the new compression map. This process is known as **rehashing**.

#### Separate Chaining
Separate chaining is a simple way of dealing with collisions is to make each bucket capable of storing more than one item. This requires each bucket {% math %} A[i] {% endmath %} to be implemented as a sequence, list or vector. Each bucket can be implemented as a miniature dictionary.