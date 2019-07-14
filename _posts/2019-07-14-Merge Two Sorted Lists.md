---
layout: post
title: "Merge Two Sorted Lists 合并两个有序链表"
subtitle: ""
date: 2019-07-14 21:32
author: "zsz"
catalog: true
tags: 
      - leetcode
      - python
      - algorithm
      - Linked List 链表
      

---






#### 合并两个有序链表

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

Example:

Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4























解法1:

先判断l1/l2是否为空，若一个为空直接返回另一个。

比较l1和l2 起点，把较小值给newHead。







##### Solution:

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        
        if l1 == None:
            return l2
        if l2 == None:
            return l1
        
        newHead = l1 if l1.val < l2.val else l2
        
        pTmp1 = l1
        pTmp2 = l2
        
        if newHead == l1:
            pTmp1 = pTmp1.next
        else:
            pTmp2 = pTmp2.next
        
        previousPointer = newHead
        
        while pTmp1 and pTmp2:
            if pTmp1.val < pTmp2.val:
                previousPointer.next = pTmp1
                previousPointer = pTmp1
                pTmp1 = pTmp1.next
            else:
                previousPointer.next = pTmp2
                previousPointer = pTmp2
                pTmp2 = pTmp2.next
                
        if pTmp1 == None:
            previousPointer.next = pTmp2
        if pTmp2 == None:
            previousPointer.next = pTmp1
            
        return newHead
                         
```



![pic](http://ww2.sinaimg.cn/large/006tNc79gy1g4zg7epgeej30ug0jsmzb.jpg)


