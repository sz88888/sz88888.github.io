---
layout: post
title: "Climbing Stairs 爬楼梯"
subtitle: ""
date: 2019-06-22 21:32
author: "zsz"
catalog: true
tags: 
      - leetcode
      - python
      - algorithm
      - Dynamic Planning 动态规划
      

---






#### 爬楼梯

假设你正在爬楼梯。需要 n 阶你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

注意：给定 n 是一个正整数。

示例 1：

输入： 2

输出： 2

解释： 有两种方法可以爬到楼顶。
1.  1 阶 + 1 阶
2.  2 阶
示例 2：

输入： 3

输出： 3

解释： 有三种方法可以爬到楼顶。
1.  1 阶 + 1 阶 + 1 阶
2.  1 阶 + 2 阶
3.  2 阶 + 1 阶














##### Solution:

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        if n ==1:
            return 1
        if n ==2:
            return 2
        first = 1
        second = 2
        for i in range(2, n):
            
            first, second = second, first + second
            
        return second

                
```
到达第n级阶梯的方法是由到达前两级阶梯的方法数组成的。例如，到达第三级阶梯一共有几种方法？ 到达第三级，可以从第二级走一步或者第一级走两步，共两种方法；到达第二级有两种方法，到达第一级有一种方法，所以到达第三级有 **两种（第二级的）** + **一种（第一级的）** = **三种**。

f(n) = f(n-1) + f(n-2)

可以看出这是一个斐波那契数列。

for循环里的 a,b = b, a+b 相当于每次把等式在数轴上往右移动一步。



![pic](http://ww2.sinaimg.cn/large/006tNc79gy1g4ajm8wchuj30uw0qmq6g.jpg)


