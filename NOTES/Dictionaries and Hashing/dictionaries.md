# Dictionaries

A dictionary is a data repository designed to effectively perform the search operation. The user assigns keys to data elements and uses them to perform search, insert and remove operations. We store key-element pairs {% math %} (k, e) {% endmath %} called **items** into a dictionary.

## Unordered Dictionaries
In the most general case, we can allow multiple elements to have the same key - however this is not advantageous in some applications, for example, multiple users with the said ID would be confusing.

In the cases when keys are unique, a key associated to an object can be regarded as an address of this object. Such dictionaries are referred to as **associative stores**.

### Abstract Data Type
As an abstract data type, a dictionary supports the following methods.

| Method Name | Description |
| ----------- | ----------- |
| `findElement(k)` | return an element {% math %} e {% endmath %} with key {% math %} k {% endmath %} if it exists, else `NO_SUCH_KEY` |
| `insertItem(k, e)` | insert an item with element {% math %} e {% endmath %} with key {% math %} k {% endmath %}|
| `removeElement(k)` | removes an element with key {% math %} k {% endmath %} and return its element if it exists, else `NO_SUCH_KEY` |

### Log Files
One simple way of representing an unordered dictionary is by an unsorted sequence {% math %} S {% endmath %}, implemented itself by a vector or list that stores the keys and its corresponding elements. Such implementation is referred to as a **log file** or **audit trial**. This implementation is suitable for storing a small amount of data that does not change much over time.