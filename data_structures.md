# Table of Contents
- [Table of Contents](#table-of-contents)
  - [Built-in Data Structures](#built-in-data-structures)
    - [String](#string)
    - [Lists](#lists)
    - [Dictionary](#dictionary)
    - [Tuple](#tuple)
    - [Set](#set)
    - [Frozen Sets](#frozen-sets)
    - [Bytearray](#bytearray)
  - [Collections Module](#collections-module)
    - [Counters](#counters)
    - [OrderedDict](#ordereddict)
    - [DefaultDict](#defaultdict)
    - [ChainMap](#chainmap)
    - [NamedTuple](#namedtuple)
    - [Deque](#deque)
    - [UserDict](#userdict)
    - [UserList](#userlist)
    - [UserString](#userstring)
  - [Advanced Data Structures](#advanced-data-structures)
    - [Binary Tree](#binary-tree)
    - [Graph](#graph)


Data Structures are a way of organizing data so that it can be accessed more efficiently depending upon the situation.

---

## Built-in Data Structures

### String

A string is a sequence of one or more characters (letters, numbers, symbols) that can be either a constant or a variable. Made up of Unicode, strings are immutable sequences, meaning they are unchanging.

```python
def main():
    """
    >>> ss = "Sammy Shark!"
    >>> ss[6:11:1]
    'Shark'
    >>> ss[::4]
    'Sya'
    >>> ss[::-1]
    '!krahS ymmaS'
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()

```

---

### Lists

A `list` is a data structure in Python that is a mutable, or changeable, ordered sequence of elements. Each element or value that is inside of a `list` is called an item. Just as `strings` are defined as characters between quotes, lists are defined by having values between square brackets `[ ]`.

```python
sea_creatures = ['shark', 'octopus', 'fish', 'shrimp', 'anemone', 'crab']


def main():
    """
    >>> del sea_creatures[1:4]
    >>> sea_creatures
    ['shark', 'anemone', 'crab']
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Dictionary

The **dictionary** is Python’s built-in **mapping** type. Dictionaries map **keys** to **values** and these key-value pairs provide a useful way to store data in Python.

Typically used to hold data that are related, such as the information contained in an ID or a user profile, dictionaries are constructed with curly braces on either side `{ }`.

```python
sammy = {'username': 'sammy-shark', 'online': True, 'followers': 987}


def main():
    """
    >>> sammy['followers']
    987
    >>> sammy.keys()
    dict_keys(['username', 'online', 'followers'])
    >>> sammy.items()
    dict_items([('username', 'sammy-shark'), ('online', True), ('followers', 987)])
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()

```

---

### Tuple

A **tuple** is a data structure that is an **immutable**, or unchangeable, ordered sequence of elements. Because tuples are immutable, their values cannot be modified.

```sql
coral = ('blue coral', 'staghorn coral', 'pillar coral', 'elkhorn coral')


def main():
    """
    >>> coral[1:3]
    ('staghorn coral', 'pillar coral')
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Set

Python **Set** is an **unordered** collection of **unique** elements. Suppose you have a list and you need only the unique items of the list you can use Python Set. Similarly, if you need only unique items from input, Python set can help you to do so. You can add or delete items from it. You can initialize a set by placing elements in between curly braces. Like other sequences, one set can have elements of multiple data-types. Moreover, you can also create a set from a list by using `set()` function. 

```python
def main():
    """
    >>> A = set()
    >>> A.add(1)
    >>> A.add(2)
    >>> A.add(2)
    >>> A
    {1, 2}
    >>> B = set([2, 3, 4])
    >>> A.union(B)
    {1, 2, 3, 4}
    >>> A.intersection(B)
    {2}
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---


### Frozen Sets

Frozen set is just an **immutable** version of a Python set object. While elements of a set can be modified at any time, elements of the frozen set remain the same after creation.

```python
def main():
    """
    >>> vowels = ('a', 'e', 'i', 'o', 'u')
    >>> fSet = frozenset(vowels)
    >>> fSet.issubset(vowels)
    True 
    >>> fSet.add('v')
    Traceback (most recent call last):
    ...
    AttributeError: 'frozenset' object has no attribute 'add'
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod(optionflags=doctest.ELLIPSIS)
```

---

### Bytearray

The `bytearray()` method returns a bytearray object which is an array of the given bytes.

```python
def main():
    """
    >>> bytearray([2, 3, 5, 7])
    bytearray(b'\\x02\\x03\\x05\\x07')
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

----

## Collections Module

### Counters

Counter is an unordered collection where elements are stored as `Dict` keys and their count as dict value. Counter elements count can be positive, zero or negative integers. However there is no restriction on it’s keys and values. Although values are intended to be numbers but we can store other objects too.

```python
from collections import Counter


def main():
    """
    >>> Counter(['a', 'a', 'b'])
    Counter({'a': 2, 'b': 1})
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### OrderedDict

Python **OrderedDict** is a `dict` subclass that maintains the items insertion **order**. When we iterate over an OrderedDict, items are returned in the order they were inserted. A regular dictionary doesn’t track the insertion order. So when iterating over it, items are returned in an arbitrary order. When we want to make sure that items are returned in the order they were inserted, we can use OrderedDict.

```python
from collections import OrderedDict

d1 = {'a': 'A', 'b': 'B'}
d2 = {'b': 'B', 'a': 'A'}

od1 = OrderedDict({'a': 'A', 'b': 'B'})
od2 = OrderedDict({'b': 'B', 'a': 'A'})


def main():
    """
    >>> d1 == d2
    True
    >>> od1 == od2
    False
    >>> d1 == od1
    True
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### DefaultDict
DefaultDict is used to provide some default values for the key that does not exist and never raises a `KeyError`. Its objects can be initialized using `DefaultDict()` method by passing the data type as an argument.

```python
from collections import defaultdict


d = defaultdict(int)

for i in range(1, 5):
    d[i] = i


def main():
    """
    >>> d[99] = 99
    >>> d
    defaultdict(<class 'int'>, {1: 1, 2: 2, 3: 3, 4: 4, 99: 99})
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### ChainMap

A `ChainMap` encapsulates many dictionaries into a single unit and returns a **list** of dictionaries. When a key is needed to be found then all the dictionaries are searched one by one until the key is found.

```python
from collections import ChainMap

d1 = {'a': 1, 'b': 2}
d2 = {'c': 3, 'd': 4}
d3 = {'e': 5, 'f': 6}


def main():
    """
    >>> c = ChainMap(d1, d2, d3)
    >>> c
    ChainMap({'a': 1, 'b': 2}, {'c': 3, 'd': 4}, {'e': 5, 'f': 6})
    >>> c['a']
    1
    >>> c['g']
    Traceback (most recent call last):
    ...
    KeyError: 'g'
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod(optionflags=doctest.ELLIPSIS)
```

---

### NamedTuple

A `NamedTuple` returns a tuple object with names for each position which the ordinary tuples lack.

```python
from collections import namedtuple

Fish = namedtuple("Fish", ["name", "species", "tank"])


def main():
    """
    >>> sammy = Fish("Sammy", "shark", "tank-a")
    >>> sammy
    Fish(name='Sammy', species='shark', tank='tank-a')
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

In `Dataclass` all implementation is written in Python, whereas in `NamedTuple`, all of these behaviors come for free because `NamedTuple` inherits from tuple. And because the tuple structure is written in C, standard methods are faster in Nam`edTuple (*hash*, *comparing* and etc).

Note also that `Dataclass` is based on dict whereas `NamedTuple` is based on tuple. Thus, you have advantages and disadvantages of using these structures. For example, space usage is less with a `NamedTuple`, but time access is faster with a `Dataclass`.

---

### Deque

Deque (Doubly Ended Queue) is the optimized list for quicker append and pop operations from both sides of the container. It provides `O(1)` time complexity for append and pop operations as compared to the list with `O(n)` time complexity.

```python
from collections import deque


def main():
    """
    >>> de = deque([1, 2, 3])
    >>> de.append(4)
    >>> de
    deque([1, 2, 3, 4])
    >>> de.appendleft(6)
    >>> de
    deque([6, 1, 2, 3, 4])
    >>> de.pop()
    4
    >>> de
    deque([6, 1, 2, 3])
    >>> de.popleft()
    6
    >>> de
    deque([1, 2, 3])
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### UserDict

`UserDict` is a dictionary-like container that acts as a wrapper around the dictionary objects. This container is used when someone wants to create their own dictionary with some modified or new functionality. 

```python
from collections import UserDict


class CaseInsensitiveDict(UserDict):
    def __setitem__(self, key, value):
        key = str(key).lower()
        self.data[key] = value

    def __getitem__(self, key):
        key = str(key).lower()
        return self.data[key]


def main():
    """
    >>> custom_dict = CaseInsensitiveDict({'Name': 'Nik', 'Age': 33})
    >>> custom_dict['name'], custom_dict['Age']
    ('Nik', 33)
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### UserList

`UserList` is a list-like container that acts as a wrapper around the list objects. This is useful when someone wants to create their own list with some modified or additional functionality.

```python

from collections import UserList


class NumberList(UserList):
    def __init__(self, iterable):
        super().__init__(
            item for item in iterable if type(item) in [int, float])

    def __setitem__(self, index, item):
        if type(item) in [int, float]:
            self.data[index] = item
        else:
            raise TypeError('Item must be a number.')

    def append(self, item):
        if type(item) in [int, float]:
            self.data.append(item)
        else:
            raise TypeError('Item must be a number.')

    def square_values(self):
        for item in self.data:
            print(item ** 2)


def main():
    """
    >>> custom_list = NumberList([1, 2, 3, 'four'])
    >>> custom_list
    [1, 2, 3]
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### UserString

`UserString` is a string-like container and just like UserDict and UserList, it acts as a wrapper around string objects. It is used when someone wants to create their own strings with some modified or additional functionality. 

```python
import re
from collections import UserString


class FunnyString(UserString):
    def __init__(self, sequence):
        self.data = re.sub(r'[^\w\s]', '', sequence)

    def funnify(self):
        funny = ""
        for idx in range(len(self.data)):
            if not idx % 2:
                funny += self.data[idx].upper()
            else:
                funny += self.data[idx].lower()
        return funny


def main():
    """
    >>> text = FunnyString('Hello! Have a nice day!')
    >>> text.funnify()
    'HeLlO HaVe a nIcE DaY'
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()

```

---

## Advanced Data Structures

### Binary Tree
A tree is a  hierarchical data structure that looks like the below figure

```python
      tree
     ----
      j    <-- root
    /   \
   f      k  
 /   \      \
a     h      z    <-- leaves
```
The topmost node of the tree is called the **root** whereas the bottommost nodes or the nodes with no children are called the **leaf** nodes.

A Binary Tree node contains the following parts.

- Data
- Pointer to left child
- Pointer to the right child

```python
class Node:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.val = key


def print_pre_order(root):
    if root:
        print(root.val)
        print_pre_order(root.left)
        print_pre_order(root.right)


def main():
    """
    >>> root = Node(1)
    >>> root.left = Node(2)
    >>> root.right = Node(3)
    >>> root.left.left = Node(4)
    >>> print_pre_order(root)
    1
    2
    4
    3
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()

```
```shell
      tree
     ----
      1    <-- root
    /   \
   2     3  
  /  
 4
```

---

### Graph
A `Graph` is a nonlinear data structure consisting of **nodes** and **edges**. The **nodes** are sometimes also referred to as vertices and the **edges** are lines or arcs that connect any two **nodes** in the `Graph`. More formally a `Graph` can be defined as a finite set of vertices(or nodes) and a set of edges that connect a pair of nodes.

![graph](https://github.com/fullmetaltac/interview_questions/assets/5435980/e76f0322-36e4-4289-b681-2cf5473ef060)

```python
from collections import defaultdict


class Graph:

    def __init__(self):
        self.graph = defaultdict(list)

    def addEdge(self, u, v):
        self.graph[u].append(v)

    def DFSUtil(self, v, visited):

        visited.add(v)
        print(v, end=' ')

        for neighbour in self.graph[v]:
            if neighbour not in visited:
                self.DFSUtil(neighbour, visited)

    def depth_first_search(self, v):
        visited = set()
        self.DFSUtil(v, visited)

    def breadth_first_search(self, s):
        visited = [False] * (max(self.graph) + 1)
        queue = []
        queue.append(s)
        visited[s] = True

        while queue:
            s = queue.pop(0)
            print(s, end=" ")

            for i in self.graph[s]:
                if visited[i] == False:
                    queue.append(i)
                    visited[i] = True


g = Graph()
g.addEdge(0, 1)
g.addEdge(0, 2)
g.addEdge(1, 2)
g.addEdge(2, 0)
g.addEdge(2, 3)
g.addEdge(3, 3)


def main():
    """
    >>> g.breadth_first_search(2)
    2 0 3 1 
    >>> g.depth_first_search(2)
    2 0 1 3 
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()

```

---
