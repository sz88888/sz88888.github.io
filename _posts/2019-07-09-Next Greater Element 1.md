---
layout: post
title: "Next Greater Element 1 下一个更大的元素 1"
subtitle: ""
date: 2019-07-09 21:32
author: "zsz"
catalog: true
tags: 
      - leetcode
      - python
      - algorithm
      - Stack 栈
      

---






#### 下一个更大的元素

给定两个没有重复元素的数组 nums1 和 nums2 ，其中nums1 是 nums2 的子集。找到 nums1 中每个元素在 nums2 中的下一个比其大的值。

nums1 中数字 x 的下一个更大元素是指 x 在 nums2 中对应位置的右边的第一个比 x 大的元素。如果不存在，对应位置输出-1。

示例 1:

输入: nums1 = [4,1,2], nums2 = [1,3,4,2].
输出: [-1,3,-1]
解释:
    对于num1中的数字4，你无法在第二个数组中找到下一个更大的数字，因此输出 -1。
    对于num1中的数字1，第二个数组中数字1右边的下一个较大数字是 3。
    对于num1中的数字2，第二个数组中没有下一个更大的数字，因此输出 -1。
示例 2:

输入: nums1 = [2,4], nums2 = [1,2,3,4].
输出: [3,-1]
解释:
    对于num1中的数字2，第二个数组中的下一个较大数字是3。
    对于num1中的数字4，第二个数组中没有下一个更大的数字，因此输出 -1。
注意:

nums1和nums2中所有元素是唯一的。
nums1和nums2 的数组大小都不超过1000。



















解法1:

两层循环来判断，把nums1里的数对应在nums2中，往后找第一个大于它的，找到了就结束这层循环并将此数加入结果列表，要是一直没找到就返回最开始设置的默认值-1。




##### Solution:

```python
class Solution:
    def nextGreaterElement(self, nums1: List[int], nums2: List[int]) -> List[int]:
        res = []
        for i in nums1:
            greater = -1
            for j in nums2[nums2.index(i) : ]:
                if j > i:
                    greater = j
                    break
            res.append(greater)
        return res                     
```



![pic](http://ww2.sinaimg.cn/large/006tNc79gy1g4tpvhjna4j30uc0hs40d.jpg)


