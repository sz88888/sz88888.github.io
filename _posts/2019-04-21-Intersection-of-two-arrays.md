---
layout: post
title: "leetcode-349 Intersection of two arrays 两个数组的交集"
subtitle: ""
date: 2019-05-02 21:32
author: "zsz"
catalog: true
tags: 
      - leetcode
      - python
      - algorithm
      - Binary Search 二分查找

---





#### Intersection of two arrays

Given two arrays, write a function to compute their intersection.

Example 1:

Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2]
Example 2:

Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [9,4]
Note:

Each element in the result must be unique.
The result can be in any order. 



##### Solution:

```python
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        results=[]
        nums1 = list(set(nums1))
        nums2 = list(set(nums2))
        if len(nums1) <= len(nums2):
            for i in range(len(nums1)):
                if nums1[i] in nums2:
                    results.append(nums1[i])
        else:
            for i in range(len(nums2)):
                if nums2[i] in nums1:
                    results.append(nums2[i])
        return results
                

                
```



![pic](https://ws3.sinaimg.cn/large/006tNc79gy1g2op4qmm9xj30sy096q4h.jpg)


