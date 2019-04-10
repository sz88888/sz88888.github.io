---
layout: post
title: "leetcode-9 Palindrome Number 回文"
subtitle: ""
date: 2019-03-10 21:32
author: "zsz"
catalog: true
tags: 
      - leetcode
      - python
      - algorithm
      - Palindrome 回文

---





#### Palindrome Number

判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。

示例 1:

输入: 121
输出: true
示例 2:

输入: -121
输出: false
解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。
示例 3:

输入: 10
输出: false
解释: 从右向左读, 为 01 。因此它不是一个回文数。
进阶:

你能不将整数转为字符串来解决这个问题吗？


##### Solution:

```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x<0 or (x%10 == 0  and x!=0) :
            return False   #负数都不是回文，末位是0的不是回文除了0
        r=0    
        
        while x>r:
            r = r*10 + x%10  #r增加翻转的1位数
            x = x//10   #向下取整  x减少翻转的一位数
            
        if x == r or x==r//10:   #如果位数是奇数，就把中间的那位去掉
            return True
        else:
            return False
            
        
```

没有用到字符串

![pic](https://ws1.sinaimg.cn/large/006tNc79gy1g1xt1sn18pj30u009sq4e.jpg)

