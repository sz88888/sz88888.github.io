---
layout: post
title: "Binary Tree Inorder Traversal 二叉树中序遍历"
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






#### 二叉树中序遍历

给定一个二叉树，返回它的中序 遍历。

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

class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        answer = []
        def inTra(root):
            if root == None:
                return None
            
            inTra(root.left)
            answer.append(root.val)
            inTra(root.right)
        inTra(root)   
        return answer
                                     
```



![pic](http://ww4.sinaimg.cn/large/006tNc79gy1g58qaefn6cj30tk06c756.jpg)

解法2，迭代：

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        answer = []
        
        def inTra(root):
            if not root:
                return root
            stack = []
            tmpNode = root
            while tmpNode or stack:
                while tmpNode:
                    stack.append(tmpNode)                    
                    tmpNode = tmpNode.left
                node = stack.pop()
                answer.append(node.val)
                tmpNode = node.right
        inTra(root)
        return answer
```

![pic](http://ww2.sinaimg.cn/large/006tNc79gy1g58qnr4xdrj30rq06a3zf.jpg)

