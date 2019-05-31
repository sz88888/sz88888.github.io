---
layout: post
title: "leetcode-007 Reverse Integer 整数反转"
subtitle: ""
date: 2019-05-30 21:32
author: "zsz"
catalog: true
tags: 
      - leetcode
      - python
      - algorithm
      

---





#### Reverse Integer

Given a 32-bit signed integer, reverse digits of an integer.

Example 1:

Input: 123
Output: 321

Example 2:

Input: -123
Output: -321

Example 3:

Input: 120
Output: 21
Note:
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.





##### Solution:

```python
class Solution:
    def reverse(self, x: int) -> int:
        if x==0:
            return x
        s=str(x)
        i=0
        s=s[::-1]
        if s[-1]=='-':
            a=int('-'+s.lstrip('0').rstrip('-'))
        else:
            a=int(s.lstrip('0').rstrip('-'))
        if a<=2**31-1 and a>=-2**(31):
            return(a)
        else:
            return(0)
                

                
```



![pic](https://ws1.sinaimg.cn/large/006tNc79gy1g3l2cak5wlj30ua08uabg.jpg)


