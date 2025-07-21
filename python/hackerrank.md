# Table of Contents
- [Table of Contents](#table-of-contents)
  - [Strings](#strings)
    - [The Minion Game](#the-minion-game)
  - [Regex and Parsing](#regex-and-parsing)
    - [Validating Credit Card Numbers](#validating-credit-card-numbers)
  - [Date and Time](#date-and-time)
    - [Time Delta](#time-delta)
  - [References:](#references)

---

## Strings

### The Minion Game

Kevin and Stuart want to play the '**The Minion Game**'.

**Game Rules**

Both players are given the same string, **S**.
Both players have to make substrings using the letters of the string **S**.
Stuart has to make words starting with consonants.
Kevin has to make words starting with vowels.
The game ends when both players have made all possible substrings.

**Scoring**
A player gets +1 point for each occurrence of the substring in the string **S**.

**For Example**:
String **S**  = BANANA
Kevin's vowel beginning word = ANA
Here, ANA occurs twice in BANANA. Hence, Kevin will get 2 Points.

*Sample Input*
```
BANANA
```

*Sample Output*
```
Stuart 12
```
*Solution*
```python
def minion_game(string: str):
    VOWELS = ["A", "E", "I", "O", "U"]
    n = len(string)
    k_score, s_score = 0, 0

    for i in range(n):
        if string[i] in VOWELS:
            k_score += n - i
        else:
            s_score += n - i

    if k_score > s_score:
        print(f"Kevin {k_score}")
    elif k_score < s_score:
        print(f"Stuart {s_score}")
    else:
        print("Draw")


if __name__ == "__main__":
    s = input()
    minion_game(s)
```


## Regex and Parsing

### Validating Credit Card Numbers

You and Fredrick are good friends. Yesterday, Fredrick received **N** credit cards from **ABCD Bank**.  
He wants to verify whether his credit card numbers are valid or not. You happen to be great at regex so he is asking for your help!

A valid credit card from **ABCD Bank** has the following characteristics:

- It must start with a 4, 5 or 6 .
- It must contain exactly 16 digits.
- It must only consist of digits (0-9).
- It may have digits in groups of 4, separated by one hyphen "-".
- It must **NOT** use any other separator like ' ' , '_', etc.
- It must **NOT** have 4 or more consecutive repeated digits.

*Sample Input*
```
6
4123456789123456
5123-4567-8912-3456
61234-567-8912-3456
4123356789123456
5133-3367-8912-3456
5123 - 3567 - 8912 - 3456
```

*Sample Output*
```
Valid
Valid
Invalid
Valid
Invalid
Invalid
```

*Solution*
```python
import re

n = int(input())
pattern = r"^(?!.*(.)(-?\1){3})[456]\d{3}(-?\d{4}){3}$"

for _ in range(n):
    result = re.match(pattern, input())

    print("Valid" if result else "Invalid")
```


## Date and Time

### Time Delta

When users post an update on social media,such as a URL, image, status update etc., other users in their network
are able to view this new post on their news feed. Users can also see exactly when the post was published, i.e, how many hours, minutes or seconds ago.

Since sometimes posts are published and viewed in different time zones, this can be confusing. You are given two
timestamps of one such post that a user can see on his newsfeed in the following format:  
`Day dd Mon yyyy hh:mm:ss +xxxx`

Here +xxxx represents the time zone. Your task is to print the absolute difference (in seconds) between them.

*Input Format*

The first line contains $T$, the number of testcases.
Each testcase contains $2$ lines, representing time $t_1$ and $t_2$ time .

*Constraints*
1. Input contains only valid timestamps
1. $years \leq 3000$

*Output Format*
Print the absolute difference $(t_1 - t_2)$ in seconds.

*Sample Input*
```
2
Sun 10 May 2015 13:54:36 -0700
Sun 10 May 2015 13:54:36 -0000
Sat 02 May 2015 19:54:36 +0530
Fri 01 May 2015 13:54:36 -0000
```

*Sample Output*
```
25200
88200
```

*Solution*
```python
import os

from datetime import datetime

date_format = "%a %d %b %Y %H:%M:%S %z"


def time_delta(t1, t2):
    d1 = datetime.strptime(t1, date_format)
    d2 = datetime.strptime(t2, date_format)
    if d2 < d1:
        return str(int((d1 - d2).total_seconds()))
    else:
        return str(int((d2 - d1).total_seconds()))


if __name__ == "__main__":
    fptr = open(os.environ["OUTPUT_PATH"], "w")
    t = int(input())

    for t_itr in range(t):
        t1 = input()
        t2 = input()
        delta = time_delta(t1, t2)
        fptr.write(delta + "\n")
    fptr.close()
```

## References:
- https://www.hackerrank.com/
