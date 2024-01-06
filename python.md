# Table of Contents
- [Table of Contents](#table-of-contents)
  - [Syntax](#syntax)
  - [Strings](#strings)
  - [Files](#files)
  - [Functions](#functions)
  - [Collections](#collections)
  - [OOP](#oop)
  - [Concurrency](#concurrency)
  - [Environment](#environment)
  - [Built-in](#built-in)

## Syntax

* ***What is the `//` operator?***

In Python, floor division is a mathematical operation that rounds down the result of a division operation to the nearest integer. 

```python
def main():
    """
    # Integer Division
    >>> print(5/2)
    2.5
    
    # Floor Division
    >>> print(5//2)
    2
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()

```

## Strings

* ***What is the split function used for?***

The split function breaks the string into shorter strings using the defined separator. It returns the list of all the words present in the string.

```python
cars = 'BMW-Tesla-Range Rover'


def main():
    """
    >>> print(cars.split('-'))
    ['BMW', 'Tesla', 'Range Rover']
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

## Files

## Functions

* ***What is the lambda function?***

An anonymous function is known as a lambda function. This function can have only one statement but can have any number of parameters.

```python
greet_user = lambda name : print('Hey there,', name)


def main():
    """
    >>> greet_user('Delilah')
    Hey there, Delilah
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()

```

---

* ***What are Python decorators?***

A decorator is a design pattern in Python that allows a user to add new functionality to an existing object without modifying its structure.

**Example 1 - Simple decorator**

```python
def make_pretty(func):
    def inner():
        print("I got decorated")

        func()
    return inner


def ordinary():
    print("I am ordinary")


decorated_func = make_pretty(ordinary)


def main():
    """
    >>> decorated_func()
    I got decorated
    I am ordinary
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()

```

**Example 2 - Decorating Functions with Parameters**

```python
def smart_divide(func):
    def inner(a, b):
        print("I am going to divide", a, "and", b)
        if b == 0:
            print("Whoops! cannot divide")
            return

        return func(a, b)
    return inner


@smart_divide
def divide(a, b):
    print(a/b)


def main():
    """
    >>> divide(2,5)
    I am going to divide 2 and 5
    0.4

    >>> divide(2,0)
    I am going to divide 2 and 0
    Whoops! cannot divide
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()

```

**Example 3 - Chaining Decorators in Python**

```python
def star(func):
    def inner(*args, **kwargs):
        print("*" * 15)
        func(*args, **kwargs)
        print("*" * 15)
    return inner


def percent(func):
    def inner(*args, **kwargs):
        print("%" * 15)
        func(*args, **kwargs)
        print("%" * 15)
    return inner


@star
@percent
def printer(msg):
    print(msg)


def main():
    """
    >>> printer("Hello")
    ***************
    %%%%%%%%%%%%%%%
    Hello
    %%%%%%%%%%%%%%%
    ***************
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

* ***What is the `map()` function used for in Python?***

The `map()` function applies a given function to each element of an iterable (`list`, `tuple` etc.) and returns an iterator containing the results.

```python
num1, num2 = [4, 5, 6], [5, 6, 7]

result = map(lambda n1, n2: n1+n2, num1, num2)


def main():
    """
    >>> print(list(result))
    [9, 11, 13]
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()

```

---

* ***What is the `filter()` function used for in Python?***

The `filter()` function selects elements from an iterable (`list`, `tuple` etc.) based on the output of a function.
The function is applied to each element of the iterable and if it returns True, the element is selected by the `filter()` function.

```python
num1, num2 = [4, 5, 6], [5, 6, 7]

result = map(lambda n1, n2: n1+n2, num1, num2)


def main():
    """
    >>> print(list(result))
    [9, 11, 13]
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()

```

---

## Collections

* ***What is slicing in Python?***

Slicing refers to the mechanism to select the range of items from sequence types like lists, tuples, strings

```python
py_string = 'Python'
py_list = ['P', 'y', 't', 'h', 'o', 'n']
py_tuple = ('P', 'y', 't', 'h', 'o', 'n')


def main():
    """
    >>> # stop = 3
    >>> py_string[slice(3)] 
    'Pyt'
    >>> # stop = 3
    >>> py_string[:3]
    'Pyt'
    >>> # start = 1, stop = 6, step = 2
    >>> py_string[slice(1, 6, 2)] 
    'yhn'
    >>> py_list[slice(-1, -4, -1)]
    ['n', 'o', 'h']
    >>> py_tuple[slice(-1, -5, -2)]
    ('n', 'h')
    """


if __name__ == "__main__":
    import doctest
```

* ***Differentiate between list and tuple?***

1. The literal syntax of tuples is shown by parentheses `()` whereas the literal syntax of lists is shown by square brackets `[]` .
2. Lists has variable length, tuple has fixed length.
3. List has mutable nature, tuple has immutable nature.
4. List has more functionality than the tuple.

*Mutable List vs Immutable Tuples:*

List has mutable nature i.e., list can be changed or modified after its creation according to needs whereas tuple has immutable nature i.e., tuple can’t be changed or modified after its creation.

```python
list_num = [1, 2, 3, 4]
tup_num = (1, 2, 3, 4)


def main():
    """
    >>> list_num[2] = 5
    >>> print(list_num)
    [1, 2, 5, 4]
    >>> tup_num[2] = 5
    Traceback (most recent call last):
    ...
    TypeError: 'tuple' object does not support item assignment
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod(optionflags=doctest.ELLIPSIS)

```

*Size Comparison:*

Tuples operation has smaller size than that of list, which makes it a bit faster but not that much to mention about until you have a huge number of elements.

```python
a = (1, 2, 3, 4, 5, 6, 7, 8, 9, 0)
b = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]


def main():
    """
    >>> print('a =', a.__sizeof__())
    a = 104
    >>> print('b =', b.__sizeof__())
    b = 120
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()

```
## OOP

* ***What is monkey patching in Python?***

The dynamic modifications made to a class or module at runtime are termed as monkey patching in Python

```python
class Victim:
    def introduce(self):
        return self.__class__.__name__


def main():
    """
    >>> print(Victim().introduce())
    Victim
    >>> Victim.introduce = lambda self : "Patched"
    >>> print(Victim().introduce())
    Patched
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()

```

## Concurrency

## Environment
* ***What is `PYTHONPATH`?***

`PYTHONPATH` is a special environment variable that provides guidance to the Python interpreter about where to find various libraries and applications.

---

## Built-in

* ***What are the Python built-in data types?***

| Data Types |           Classes            |                       Description |
| ---------- | :--------------------------: | --------------------------------: |
| Numeric    |     int, float, complex      |              holds numeric values |
| String     |             str              |      holds sequence of characters |
| Sequence   |      list, tuple, range      |         holds collection of items |
| Mapping    |             dict             | holds data in key-value pair form |
| Boolean    |             bool             |    holds either `True` or `False` |
| Set        |       set, frozeenset        |   hold collection of unique items |
| Binary     | bytes, bytearray, memoryview |       hold collection binary data |

---

* ***Explain memory managed in Python?***

Python private heap space takes place of memory management in Python. It contains all Python objects and data structures. The interpreter is responsible to take care of this private heap and the programmer does not have access to it. The Python memory manager is responsible for the allocation of Python heap space for Python objects. The programmer may access some tools for the code with the help of the core API. Python also provides an inbuilt garbage collector, which recycles all the unused memory and frees the memory and makes it available to heap space.

---