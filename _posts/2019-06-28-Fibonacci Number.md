---
layout: post
title: "Fibonacci Number 斐波那契数列"
subtitle: ""
date: 2019-06-28 21:32
author: "zsz"
catalog: true
tags: 
      - leetcode
      - python
      - algorithm
      - array
      

---






#### Fibonacci

The Fibonacci numbers, commonly denoted F(n) form a sequence, called the Fibonacci sequence, such that each number is the sum of the two preceding ones, starting from 0 and 1. That is,

F(0) = 0,   F(1) = 1
F(N) = F(N - 1) + F(N - 2), for N > 1.
Given N, calculate F(N).

 

Example 1:

Input: 2

Output: 1

Explanation: F(2) = F(1) + F(0) = 1 + 0 = 1.

Example 2:

Input: 3

Output: 2

Explanation: F(3) = F(2) + F(1) = 1 + 1 = 2.

Example 3:

Input: 4

Output: 3

Explanation: F(4) = F(3) + F(2) = 2 + 1 = 3.
 


















##### Solution:

```python
class Solution:
    def fib(self, N: int) -> int:
        if N == 0:
            return 0
        elif N == 1:
            return 1
        a = 0
        b = 1
        for i in range(2, N+1):
            a, b = b, a + b
        return b

                
```
题目也可以变为跳台阶，一次只可以跳一级或者两级台阶，跳到第N级台阶一共有多少种跳法？

跳到第N级台阶的方法数为：跳到第N-1级的方法数 + 跳到第N-2级台阶的方法数。

即 f(N) = f(N-1) + f(N-2)

把前两位数零和一设好，循环往前赋值，range要从2到N（即N+1）。


![pic](http://ww4.sinaimg.cn/large/006tNc79gy1g4hj745633j30ug0gmwge.jpg)


