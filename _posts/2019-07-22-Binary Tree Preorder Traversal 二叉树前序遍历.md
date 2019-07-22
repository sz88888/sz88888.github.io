---
layout: post
title: "Binary Tree Preorder Traversal 二叉树前序遍历"
subtitle: ""
date: 2019-07-22 21:32
author: "zsz"
catalog: true
tags: 
      - leetcode
      - python
      - algorithm
      - 树
      

---






#### 二叉树前序遍历

给定一个二叉树，返回它的前序 遍历。

示例:

输入: [1,null,2,3]
   1
    \
     2
    /
   3

输出: [1,3,2]
进阶: 递归算法很简单，你可以通过迭代算法完成吗？







解法1， 递归:



##### Solution:

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

#先来递归

class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        ans = []
        def PT(root):
            if not root:
                return None
            ans.append(root.val)
            PT(root.left)
            PT(root.right)
        PT(root)
        return ans
                                     
```



![pic](http://ww3.sinaimg.cn/large/006tNc79gy1g596eux0vsj30os064my0.jpg)

解法2，迭代：

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

#再来迭代

class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        ans = []
        def PT(root):
            if not root:
                return None
            stack = []
            tmpNode = root
            while tmpNode or stack:
                while tmpNode:
                    stack.append(tmpNode)
                    ans.append(tmpNode.val)
                    tmpNode = tmpNode.left
                node = stack.pop()
                tmpNode = node.right
        PT(root)
        return ans
                    
```

![pic](http://ww3.sinaimg.cn/large/006tNc79gy1g596q44bkxj30ry05idgq.jpg)

