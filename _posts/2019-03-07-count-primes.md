---
layout: post
title: "leetcode-204 Count Primes 质数计数"
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
1：

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

This solution could work but time limit exceeded. Complexity of this solution is O(n<sup>2</sup>).超时了。

2:
如果一个数是合数，那么它的最小质因数肯定小于等于它的平方根。
因为如果最小质因数已经大于平方根了，那么大的质因数就要大于平方根，两个质因数相乘肯定大于这个数。所以只需要判断这个数是否能被小于其平方根的所有数整除。
```

    def countPrimes(self, n: int) -> int:
        if n <= 2:
            return 0
        else:
            res = 0
        for i in range(2, n):
            isPrime = 0
            for j in range(2, int(i**0.5)+1):
                if i%j ==0:
                    isPrime = 1
            if isPrime == 0:
                res += 1
        return res
还是超时了。。

3:
