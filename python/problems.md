# Table of Contents
- [Table of Contents](#table-of-contents)
  - [Easy](#easy)
    - [Reverse String](#reverse-string)
    - [Palindrome Check](#palindrome-check)
    - [FizzBuzz](#fizzbuzz)
    - [Find Max in List](#find-max-in-list)
    - [Sum of Digits](#sum-of-digits)
    - [Count Vowels](#count-vowels)
    - [Factorial (recursive)](#factorial-recursive)
    - [Find Duplicates in List](#find-duplicates-in-list)
    - [Check Anagrams](#check-anagrams)
    - [Merge Two Sorted Lists](#merge-two-sorted-lists)
  - [Medium](#medium)
    - [Valid Parentheses](#valid-parentheses)
    - [Two Sum](#two-sum)
    - [Remove Duplicates from List](#remove-duplicates-from-list)
    - [Binary Search](#binary-search)
    - [Longest Common Prefix](#longest-common-prefix)
    - [Group Anagrams](#group-anagrams)
    - [Rotate Matrix 90°](#rotate-matrix-90)
    - [First Unique Character](#first-unique-character)
    - [Top K Frequent Elements](#top-k-frequent-elements)
    - [Implement Stack with Min](#implement-stack-with-min)
  - [Hard](#hard)
    - [LRU Cache](#lru-cache)
    - [Serialize / Deserialize Binary Tree](#serialize--deserialize-binary-tree)
    - [Word Ladder (BFS)](#word-ladder-bfs)
    - [Longest Substring Without Repeating Characters](#longest-substring-without-repeating-characters)
    - [Median of Two Sorted Arrays](#median-of-two-sorted-arrays)
    - [Find All Permutations](#find-all-permutations)
    - [N-Queens](#n-queens)
    - [Sudoku Solver](#sudoku-solver)
    - [Knapsack 0/1 (DP)](#knapsack-01-dp)
    - [Max Path Sum in Binary Tree](#max-path-sum-in-binary-tree)

## Easy

### Reverse String

```python
def reverse_string(s):
    return s[::-1]


def main():
    """
    >>> reverse_string("test")
    'tset'
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Palindrome Check

```python 
def is_palindrome(s):
    return s == s[::-1]


def main():
    """
    >>> is_palindrome("test")
    False
    >>> is_palindrome("anna")
    True
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### FizzBuzz

```python
def fizzbuzz(n):
    return [
        "Fizz" * (i % 3 == 0) + "Buzz" * (i % 5 == 0) or str(i) for i in range(1, n + 1)
    ]


def main():
    """
    >>> fizzbuzz(15)
    ['1', '2', 'Fizz', '4', 'Buzz', 'Fizz', '7', '8', 'Fizz', 'Buzz', '11', 'Fizz', '13', '14', 'FizzBuzz']
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Find Max in List

```python
def find_max(nums):
    return max(nums)


def main():
    """
    >>> find_max([15, 3, 9, 27, 5])
    27
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Sum of Digits

```python
def sum_digits(n):
    return sum(int(d) for d in str(abs(n)))


def main():
    """
    >>> sum_digits(12345)
    15
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()

```

---

### Count Vowels

```python
def count_vowels(s):
    return sum(1 for ch in s.lower() if ch in "aeiou")


def main():
    """
    >>> count_vowels("Hello World")
    3
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Factorial (recursive)

```python
def factorial(n):
    return 1 if n == 0 else n * factorial(n - 1)


def main():
    """
    >>> factorial(7)
    5040
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Find Duplicates in List

```python
def find_duplicates(lst):
    seen, dupes = set(), set()
    for x in lst:
        if x in seen:
            dupes.add(x)
        seen.add(x)
    return list(dupes)


def main():
    """
    >>> find_duplicates([1,2,3,4,5,1,2,3])
    [1, 2, 3]
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Check Anagrams

```python
def is_anagram(a, b):
    return sorted(a) == sorted(b)


def main():
    """
    >>> is_anagram('listen', 'silent')
    True
    >>> is_anagram('dog', 'good')
    False
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Merge Two Sorted Lists

```python
def merge_sorted(a, b):
    i = j = 0
    res = []
    while i < len(a) and j < len(b):
        res.append(a[i] if a[i] < b[j] else b[j])
        if a[i] < b[j]:
            i += 1
        else:
            j += 1
    return res + a[i:] + b[j:]


def main():
    """
    >>> merge_sorted([1, 4, 6, 10], [2, 5, 7, 12])
    [1, 2, 4, 5, 6, 7, 10, 12]
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

## Medium

### Valid Parentheses

```python
def is_valid(s):
    stack = []
    pairs = {')': '(', ']': '[', '}': '{'}
    for ch in s:
        if ch in pairs:
            if not stack or stack.pop() != pairs[ch]: return False
        else:
            stack.append(ch)
    return not stack


def main():
    """
    >>> is_valid("{[()[]{}]}")
    True
    >>> is_valid("{[(])}")
    False
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Two Sum

```python
def two_sum(nums, target):
    seen = {}
    for i, num in enumerate(nums):
        if target - num in seen:
            return [seen[target - num], i]
        seen[num] = i


def main():
    """
    >>> two_sum([2, 7, 11, 15], 9)         
    [0, 1]
    >>> two_sum([3, 2, 4], 6)              
    [1, 2]
    >>> two_sum([-1, -2, -3, -4, -5], -8)
    [2, 4]
    >>> two_sum([1, 2, 3], 10) 
    
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Remove Duplicates from List

```python
def remove_duplicates(lst):
    return list(dict.fromkeys(lst))


def main():
    """
    >>> remove_duplicates([1, 2, 1, 7, 11, 1, 15, 15])
    [1, 2, 7, 11, 15]
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Binary Search

```python
def binary_search(arr, target):
    l, r = 0, len(arr) - 1
    while l <= r:
        m = (l + r) // 2
        if arr[m] == target:
            return m
        elif arr[m] < target:
            l = m + 1
        else:
            r = m - 1
    return -1


def main():
    """
    >>> binary_search([1, 3, 5, 7, 9], 5)
    2
    >>> binary_search([1, 2, 3, 4, 5], 1)
    0
    >>> binary_search([10, 20, 30, 40], 40)
    3
    >>> binary_search([2, 4, 6, 8], 5)
    -1
    >>> binary_search([], 1)
    -1
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Longest Common Prefix


```python
def longest_common_prefix(strs):
    if not strs:
        return ""
    for i in range(len(strs[0])):
        if any(i >= len(s) or s[i] != strs[0][i] for s in strs):
            return strs[0][:i]
    return strs[0]


def main():
    """
    >>> longest_common_prefix(["flower", "flow", "flight"])
    'fl'
    >>> longest_common_prefix(["dog", "racecar", "car"])
    ''
    >>> longest_common_prefix(["interspecies", "interstellar", "interstate"])
    'inters'
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Group Anagrams


```python
from collections import defaultdict


def group_anagrams(strs):
    res = defaultdict(list)
    for s in strs:
        res[tuple(sorted(s))].append(s)
    return list(res.values())


def main():
    """
    >>> group_anagrams(["eat", "tea", "tan", "ate", "nat", "bat"])
    [['eat', 'tea', 'ate'], ['tan', 'nat'], ['bat']]
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Rotate Matrix 90°


```python
def rotate(matrix):
    return [list(row) for row in zip(*matrix[::-1])]


def main():
    """
    >>> rotate([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
    [[7, 4, 1], [8, 5, 2], [9, 6, 3]]
    """


if __name__ == "__main__":
    import doctest

    doctest.testmod()
```

---

### First Unique Character


```python
from collections import Counter


def first_unique_char(s):
    counts = Counter(s)
    for c in s:
        if counts[c] == 1:
            return c
    return None


def main():
    """
    >>> first_unique_char("leetcode")
    'l'
    >>> first_unique_char("loveleetcode")
    'v'
    >>> first_unique_char("aabb")

    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Top K Frequent Elements


```python
from collections import Counter
import heapq


def top_k_frequent(nums, k):
    return [x for x, _ in heapq.nlargest(k, Counter(nums).items(), key=lambda x: x[1])]


def main():
    """
    >>> top_k_frequent([1,1,1,2,2,3], 2)
    [1, 2]
    >>> top_k_frequent(["a", "b", "a", "c"], 1)
    ['a']
    >>> top_k_frequent([4, 4, 4, 5, 5, 6], 3)
    [4, 5, 6]
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Implement Stack with Min

```python
class MinStack:
    def __init__(self):
        self.stack = []
        self.min_stack = []

    def push(self, val):
        self.stack.append(val)
        self.min_stack.append(min(val, self.min_stack[-1] if self.min_stack else val))

    def pop(self):
        self.stack.pop()
        self.min_stack.pop()

    def top(self):
        return self.stack[-1]

    def get_min(self):
        return self.min_stack[-1]


def main():
    """
    >>> s = MinStack()
    >>> s.push(3)
    >>> s.push(5)
    >>> s.push(2)
    >>> s.push(1)
    >>> s.get_min()
    1
    >>> s.pop()
    >>> s.get_min()
    2
    >>> s.top()
    2
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

## Hard

### LRU Cache

```python
from collections import OrderedDict


class LRUCache:
    def __init__(self, capacity: int):
        self.cache = OrderedDict()
        self.cap = capacity

    def get(self, key):
        if key not in self.cache:
            return -1
        self.cache.move_to_end(key)
        return self.cache[key]

    def put(self, key, value):
        if key in self.cache:
            self.cache.move_to_end(key)
        self.cache[key] = value
        if len(self.cache) > self.cap:
            self.cache.popitem(last=False)
```

---

### Serialize / Deserialize Binary Tree

```python
class TreeNode:
    def __init__(self, val, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right


def serialize(root):
    if not root:
        return "None"
    return f"{root.val},{serialize(root.left)},{serialize(root.right)}"


def deserialize(data):
    vals = iter(data.split(","))

    def build():
        val = next(vals)
        if val == "None":
            return None
        node = TreeNode(int(val))
        node.left = build()
        node.right = build()
        return node

    return build()
```

---


### Word Ladder (BFS)

```python
from collections import deque


def ladderLength(beginWord, endWord, wordList):
    word_set = set(wordList)
    if endWord not in word_set:
        return 0

    queue = deque([(beginWord, 1)])

    while queue:
        word, length = queue.popleft()

        for i in range(len(word)):
            for c in "abcdefghijklmnopqrstuvwxyz":
                new_word = word[:i] + c + word[i + 1 :]
                if new_word == endWord:
                    return length + 1
                if new_word in word_set:
                    queue.append((new_word, length + 1))
                    word_set.remove(new_word)

    return 0
```

---

### Longest Substring Without Repeating Characters 

```python
def length_of_longest_substring(s):
    start = max_len = 0
    seen = {}
    for i, ch in enumerate(s):
        if ch in seen and seen[ch] >= start:
            start = seen[ch] + 1
        seen[ch] = i
        max_len = max(max_len, i - start + 1)
    return max_len
```

---

### Median of Two Sorted Arrays


```python
def find_median_sorted_arrays(nums1, nums2):
    if len(nums1) > len(nums2):
        nums1, nums2 = nums2, nums1

    x, y = len(nums1), len(nums2)
    low, high = 0, x

    while low <= high:
        partitionX = (low + high) // 2
        partitionY = (x + y + 1) // 2 - partitionX

        maxLeftX = float("-inf") if partitionX == 0 else nums1[partitionX - 1]
        minRightX = float("inf") if partitionX == x else nums1[partitionX]

        maxLeftY = float("-inf") if partitionY == 0 else nums2[partitionY - 1]
        minRightY = float("inf") if partitionY == y else nums2[partitionY]

        if maxLeftX <= minRightY and maxLeftY <= minRightX:
            if (x + y) % 2 == 0:
                return (max(maxLeftX, maxLeftY) + min(minRightX, minRightY)) / 2
            else:
                return max(maxLeftX, maxLeftY)
        elif maxLeftX > minRightY:
            high = partitionX - 1
        else:
            low = partitionX + 1

    raise ValueError("Input arrays are not sorted properly")


def main():
    """
    >>> find_median_sorted_arrays([1, 2], [3, 4])
    2.5
    """


if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

---

### Find All Permutations


```python
def permutations(s):
    if len(s) == 0:
        return [""]
    res = []
    for i, ch in enumerate(s):
        for perm in permutations(s[:i] + s[i + 1 :]):
            res.append(ch + perm)
    return res
```

---

### N-Queens


```python
# TODO
```

---

### Sudoku Solver


```python
# TODO
```

---

### Knapsack 0/1 (DP)


```python
# TODO
```

---

### Max Path Sum in Binary Tree


```python
# TODO
```

---