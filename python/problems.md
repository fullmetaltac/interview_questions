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
```

---

### Palindrome Check

```python 
def is_palindrome(s):
    return s == s[::-1]
```

---

### FizzBuzz

```python
def fizzbuzz(n):
    return ["Fizz" * (i % 3 == 0) + "Buzz" * (i % 5 == 0) or str(i) for i in range(1, n + 1)]

```

---

### Find Max in List

```python
def find_max(nums):
    return max(nums)
```

---

### Sum of Digits

```python
def sum_digits(n):
    return sum(int(d) for d in str(abs(n)))

```

---

### Count Vowels

```python
def count_vowels(s):
    return sum(1 for ch in s.lower() if ch in 'aeiou')
```

---

### Factorial (recursive)

```python
def factorial(n):
    return 1 if n == 0 else n * factorial(n - 1)
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
```

---

### Check Anagrams

```python
def is_anagram(a, b):
    return sorted(a) == sorted(b)

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

```

---

### Remove Duplicates from List

```python
def remove_duplicates(lst):
    return list(dict.fromkeys(lst))

```

---

### Binary Search

```python
def binary_search(arr, target):
    l, r = 0, len(arr)-1
    while l <= r:
        m = (l + r) // 2
        if arr[m] == target: return m
        elif arr[m] < target: l = m + 1
        else: r = m - 1
    return -1
```

---

### Longest Common Prefix


```python
def longest_common_prefix(strs):
    if not strs: return ""
    for i in range(len(strs[0])):
        if any(i >= len(s) or s[i] != strs[0][i] for s in strs):
            return strs[0][:i]
    return strs[0]

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
```

---

### Rotate Matrix 90°


```python
def rotate(matrix):
    return [list(row) for row in zip(*matrix[::-1])]

```

---

### First Unique Character


```python
from collections import Counter
def first_unique(s):
    counts = Counter(s)
    for i, c in enumerate(s):
        if counts[c] == 1:
            return i
    return -1
```

---

### Top K Frequent Elements


```python
from collections import Counter
import heapq
def top_k_frequent(nums, k):
    return [x for x, _ in heapq.nlargest(k, Counter(nums).items(), key=lambda x: x[1])]

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
        if key not in self.cache: return -1
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
    if not root: return "None"
    return f"{root.val},{serialize(root.left)},{serialize(root.right)}"

def deserialize(data):
    vals = iter(data.split(","))
    def build():
        val = next(vals)
        if val == "None": return None
        node = TreeNode(int(val))
        node.left = build()
        node.right = build()
        return node
    return build()
```

---


### Word Ladder (BFS)

```python
# TODO
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
# TODO
```

---

### Find All Permutations


```python
def permutations(s):
    if len(s) == 0: return [""]
    res = []
    for i, ch in enumerate(s):
        for perm in permutations(s[:i] + s[i+1:]):
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