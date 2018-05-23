# Divide and Conquer

> Problem: Consider finding both the maximum and minimum of a sequence of integers.

The obvious method is to find the maximum by iterating through the sequence and then doing the same to find the minimum. For the maximum, we do {% math %} N - 1 {% endmath %} comparisons, and then for the minimum it is {% math %} N - 2 {% endmath %} operations, to we do a total of {% math %} 2N - 3 {% endmath %}.

#### The idea
The **divide-and-conquer** technique involves solving a problem by dividing it into one or more subproblems of smaller size, recursively solving each subproblem then combining the solutions to the subproblems to produce a solution to the original problem.

#### Example - max-and-min problem
- Divide the sequence {% math %} s {% endmath %} into {% math %} s_1 {% endmath %} and {% math %} s_2 {% endmath %}, of approximately equal size of efficiency
- Now recursively calculate the maximum and minimum of the subsequence {% math %} s_1 {% endmath %} ({% math %} max_1 {% endmath %} and {% math %} min_1 {% endmath %}) and subsequence {% math %} s_2 {% endmath %} ({% math %} max_2 {% endmath %} and {% math %} min_2 {% endmath %}).
- We can calculate the maximum and minimum of the whole sequence {% math %} s {% endmath %} as the maximum is {% math %} max(max_1, max_2) {% endmath %} and the minimum is {% math %} min(min_1, min_2) {% endmath %}.

```
Algorithm maxmin(s):
  Input: A sequence s
  Output: (max, min) pair

  if s = [x]
    return (x, x)
  if s = [x1, x2]
    if x1 > x2
      return (x1, x2)
    else
      return (x2, x1)
  else
    (s1, s2) = divide(s)
    (max1, min1) = maxmin(s1)
    (max2, min2) = maxmin(s2)
    return (max(max1, max2), min(min1, min2))
```

Let {% math %} C_N {% endmath %} be the number of integer comparisons needed on a sequence on length {% math %} N {% endmath %}. Then
{% math %}
\large
C_N = 2 \times C_{N/2} + 2
{% endmath %} and {% math %} C_1 = 0 {% endmath %} and {% math %} C_2 = 1 {% endmath %}.

It follows that {% math %} C_N = 3N / 2 - 2 {% endmath %}, which is much smaller than the previous method, which required {% math %} 2N - 3 {% endmath %}. Notice that both methods are linear, {% math %} O(N) {% endmath %}.

#### Applications
A few examples of divide-and-conquer:

- Efficient **sorting** algorithms - both mergesort and quicksort have average time complexity of {% math %} O(N\log(N)) {% endmath %}, whereas most simple general sorting algorithms are slower, {% math %} O(N^2) {% endmath %}

- Fast **integer multiplication** - integer multiplication by long multiplication is {% math %} O(N^2) {% endmath %}, but there are faster {% math %} O(N\log(N)) {% endmath %} divide-and-conquer algorithms

- Fast **matrix multiplication** - standard matrix multiplication is {% math %} O(N^3) {% endmath %}, divide-and-conquer algorithms produce algorithms in {% math %} O(N^{2.808...}) {% endmath %} and even down to {% math %} O(N^{2.376...}) {% endmath %}

- **Nearest neighbour problems** - given a set of {% math %} N {% endmath %} points in n-dimensions, find two nearest points. Divide-and-conquer algorithms are in {% math %} O(N\log(N)) {% endmath %}