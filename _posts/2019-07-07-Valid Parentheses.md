---
layout: post
title: "Valid Parentheses 有效的括号"
subtitle: ""
date: 2019-07-07 21:32
author: "zsz"
catalog: true
tags: 
      - leetcode
      - python
      - algorithm
      - Stack 栈
      

---






#### 有效的括号

给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。

有效字符串需满足：

左括号必须用相同类型的右括号闭合。
左括号必须以正确的顺序闭合。
注意空字符串可被认为是有效字符串。

示例 1:

输入: "()"
输出: true
示例 2:

输入: "()[]{}"
输出: true
示例 3:

输入: "(]"
输出: false
示例 4:

输入: "([)]"
输出: false
示例 5:

输入: "{[]}"
输出: true


















##### Solution:

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        mapping={')':'(',']':'[','}':'{'}
        for char in s:
            if char in mapping:
                
                top = stack.pop() if stack else '#'
                
                if mapping[char] != top:
                    return False
            else:
                stack.append(char)
        
        return not stack
                       
```
有效的括号条件包括：

1. 开括号和闭括号对应；
2. 对应括号间不能加载其他括号对的一半，如`([)]`

用一个栈和一个右括号对应左括号的字典，从左到右查看括号序列；
如果查看到的是左括号则压入栈，如果是右括号则取出栈顶元素；如果查看到的该元素与刚从栈顶取出的元素相对应（用字典来对应），那么就符合要求，若不对应则为无效括号。



![pic](http://ww1.sinaimg.cn/large/006tNc79gy1g4rhl7l0tlj30ss06qjs9.jpg)


