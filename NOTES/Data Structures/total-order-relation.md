# Keys and Total Order relation

A **key** is an object assigned to an element as a specific attribute that can be used to identify, rank or weight that element. We needs keys to be robustly defined, i.e. not contradicting.

## Total Order relation
We say that a set {% math %} X {% endmath %} is **totally ordered** under {% math %} \leq {% endmath %} if the following statements hold for all {% math %} a, b {% endmath %} and {% math %} c {% endmath %} in {% math %} X {% endmath %}:
- **antisymmetry**: if {% math %} a \leq b {% endmath %} and {% math %} b \leq a {% endmath %}, then {% math %} a = b {% endmath %}
- **transitivity**: if {% math %} a \leq b {% endmath %} and {% math %} b \leq c {% endmath %}, then {% math %} a \leq c {% endmath %}
- **totality**: {% math %} a \leq b {% endmath %} or {% math %} b \leq a {% endmath %}

The comparison rule that satisfies the above properties defines a linear ordering relationship among a set of keys.

In a finite collection of elements with a total order defined relation, we can define the **smallest key** {% math %} k_{min} {% endmath %} as the key for which {% math %} k_{min} \leq k {% endmath %} for any other key {% math %} k {% endmath %} in the collection.