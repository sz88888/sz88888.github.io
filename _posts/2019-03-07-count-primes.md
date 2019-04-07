---
layout: post
title: "204 Count Primes"
subtitle: ""
date: 2019-03-09 21:32
author: "zsz"
catalog: true
tags: 
      - leetcode
      - python
      - algorithm

---





#### Count Primes

Count the number of prime numbers less than a non-negative number, n.

Example:
```
Input: 10
Output: 4
Explanation: There are 4 prime numbers less than 10, they are 2, 3, 5, 7.
```

##### Solution:

```python
class Solution:
    def countPrimes(self, n: int) -> int:
        count = 0
        for i in range(2,n):
            for j in range(2,i):
                if i%j == 0:
                    break
            else:
                count += 1
        return count
        
```

This solution could work but time limit exceeded. Complexity of this solution is O(n<sup>2</sup>).

