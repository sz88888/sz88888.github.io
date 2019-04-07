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

```python
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
```        
还是超时了。。

3:

Eratosthenes 埃拉托斯特尼筛法
![gif](https://ws4.sinaimg.cn/large/006tNc79gy1g1uh63aon6g30cd0a9q6x.gif)


 1. 是质数，同时划去所有2的倍数，接着查看剩下的数 
 2. 是质数，同时划去所有3的倍数，接着查看剩下的数
 3. 一直进行到n的平方根（向上取整）。

sol2经验：只需要判断小于等于平方根的所有数


```python
    def countPrimes(self, n: int) -> int:
        if n <= 2:
            return 0
        else:
            output = [1]*n
            output[0],output[1] = 0,0
            for i in range(2,int(n**0.5)+1):
                if output[i] == 1:
                    output[i*i:n:i] = [0]*len(output[i*i:n:i])
        return sum(output)
    
```
![pic](https://ws3.sinaimg.cn/large/006tNc79gy1g1ui5ibyobj30o60iwgmm.jpg)
![pic](https://ws2.sinaimg.cn/large/006tNc79gy1g1ui5mw1x7j30ts08kta1.jpg)