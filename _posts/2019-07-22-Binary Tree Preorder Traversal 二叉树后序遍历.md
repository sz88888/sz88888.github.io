---
layout: post
title: "Binary Tree Postorder Traversal 二叉树后序遍历"
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






#### 二叉树后序遍历

给定一个二叉树，返回它的后序 遍历。

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
        def POT(root):
            if not root:
                return None
            
            POT(root.left)
            POT(root.right)
            ans.append(root.val)
        POT(root)
        return ans
                                     
```



![pic](http://ww3.sinaimg.cn/large/006tNc79gy1g598hk7h1ij30pu070ab0.jpg)

解法2，迭代：

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def postorderTraversal(self, root: TreeNode) -> List[int]:
        ans = []
        def POT(root):
            if not root:
                return None
            stack1 = []
            stack2 = []
            stack1.append(root)
            while stack1:           #stack1逆序存放了后序遍历的节点，并以该顺序压入2号栈
                node = stack1.pop()
                if node.left:
                    stack1.append(node.left)
                if node.right:
                    stack1.append(node.right)
                stack2.append(node.val)   #将节点的值压入stack2
            while stack2:           #从stack2取出时便成了正序的后序遍历
                ans.append(stack2.pop())
        POT(root)
        return ans
                    
```

![pic](http://ww2.sinaimg.cn/large/006tNc79gy1g598ew8kx0j30r006agmi.jpg)

