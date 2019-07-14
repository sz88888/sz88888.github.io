---
layout: post
title: "Reverse Linked List 反转链表"
subtitle: ""
date: 2019-07-014 21:32
author: "zsz"
catalog: true
tags: 
      - leetcode
      - python
      - algorithm
      - Linked List 链表
      

---






#### 反转链表

反转一个单链表。

示例:

输入: 1->2->3->4->5->NULL
输出: 5->4->3->2->1->NULL
进阶:
你可以迭代或递归地反转链表。你能否用两种方法解决这道题？




















解法1:

先判断是否为空或只有一个节点。

设置左中右三个点，先断开左指中，再循环将中指向左，三个点整体右移，直到右点为空，再将最后的中点指向左点。

此时中点是表头，返回之。




##### Solution:

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        if head == None:
            return None
        if head.next == None:
            return head
        
        left = head
        mid = head.next
        right = mid.next
        left.next = None
        
        while right != None:
            mid.next = left
            left = mid
            mid = right
            right = right.next
            
        mid.next = left
        
        return mid                    
```



![pic](http://ww2.sinaimg.cn/large/006tNc79gy1g4zfg2t4tfj30tw082my8.jpg)


