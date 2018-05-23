# Hash Tables

For an unordered dictionary, if the keys represent the **addresses** of the elements, we can effectively implement a dictionary using a **hash table**. The two main components of a has table are the **bucket arrays** and the **hash functions**. A bucket array for a hash table is an array {% math %} A {% endmath %} of size {% math %} N {% endmath %}, where each element of A is a container of key-element pairs and {% math %} N {% endmath %} is the capacity of the array. An element {% math %} e {% endmath %} with key {% math %} k {% endmath %} is inserted into the bucket {% math %} A[k] {% endmath %}. If keys are not unique, two elements may be mapped to the same bucket in {% math %} A {% endmath %} and in this case, we say that a **collision** has occurred.

## Hash Functions
A **hash function** {% math %} h {% endmath %} maps each key {% math %} k {% endmath %} from a dictionary to an integer in the range {% math %} [0, N - 1] {% endmath %}, where {% math %} N {% endmath %} is the bucket capacity. Instead of using {% math %} k {% endmath %} as the index of the bucket array, we use {% math %} h(k) {% endmath %}, so we store the item {% math %} (k, e) {% endmath %} in the bucket {% math %} A[h(k)] {% endmath %}.

A good hash function is one that minimises collisions as much as possible whilst evaluating {% math %} h(k) {% endmath %} at a relatively low cost. The evaluation of a hash code consists of two phases: mapping {% math %} k {% endmath %} to an integer (**hash code**), then mapping the hash code to an integer within the range of indices in a bucket array (**compression map**).

### Hash Codes
The first action performed on an aribtrary key {% math %} k {% endmath %} is to assign to it an integer value (known as the **hash code**). This integer does not need to be in the range {% math %} [0, N - 1] {% endmath %}, but the algorithm for assigning it should avoid collision. 

The range of values of {% math %} k {% endmath %} can be larger than that assumed in the hash code, for example {% math %} k {% endmath %} is a long and the hash value is a short. In this situation, we can create a hash code by taking only the lower or upper half of {% math %} k {% endmath %} as a hash code. Another method would be to sum the lower and upper halves of {% math %} k {% endmath %} (the summation hash).

#### Summation Hash Code
Consider a string of the form {% math %} (x_0 x_1 \cdots x_{k - 1}) {% endmath %} where each {% math %} x_i {% endmath %} is an ASCII character.

{% math %}
\large
\sum_{i=0}^{k-1} \text{ASCII}(x_i)
{% endmath %}

The summation hash function as defined above would produce many unwanted collisions. Clearly, two strings where one is a permutations of the other would result in the same hash.

#### Polynomial Hash Code
In the polynomial hash code function, we also take into the position of a character in the string. By choosing a constant {% math %} a (a \neq 0, 1) {% endmath %}, we can defined the hash code as follows:

{% math %}
\large
h = x_0a^{k-1} + x_1a^{k-2}+ \cdots + x_{k-2}a + x_{k-1}
{% endmath %}

Experimental studies show that good spreads of hash codes are obtained with certain choices for {% math %} a {% endmath %}, for example 33, 37, 39, 41. These values were tested on the case of 50,000 english words and each of these choices provided fewer than 7 collisions.

### Compression Maps
If the range of hash codes generated for the keys exceeds the index range of the bucket array, the attempt to write the element would cause an out-of-bounds exception, either because the index is negative or out of the range {% math %} [0, N - 1] {% endmath %}. The process of mapping an arbitrary integer to the range {% math %} [0, N - 1] {% endmath %} is called **compression**, and is the second step in evaluating the hash function.

#### Division
{% math %}
\large
h(k) = \vert k \vert \; \text{mod} \; N
{% endmath %}
This compression map is known as the **division method**. If {% math %} N {% endmath %} is a prime number, the division compression map may help spread out the hashed values. Otherwise, there is a likelihood that the patterns in the key distributions are repeated.

#### Multiply Add and Divide (MAD)
{% math %}
\large
h(k) = \vert ak + b \vert \; \text{mod} \; N
{% endmath %}
This compression map is known as the **multiply add and divide** (or MAD method), where {% math %} N {% endmath %} is a prime number and {% math %} a, b{% endmath %} are random non-negative integers selected at the time of compression, such that {% math %} a \; \text{mod} \; N \neq 0 {% endmath %}. With this compression function, the probability of collision is at most {% math %} 1/N {% endmath %}.