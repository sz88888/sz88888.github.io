---
layout: post
title: "leetcode-35 Search Insert Position 搜索插入位置"
subtitle: ""
date: 2019-03-11 21:32
author: "zsz"
catalog: true
tags: 
      - leetcode
      - python
      - algorithm
      - Binary Search 二分查找

---





#### Search Insert Position

给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

你可以假设数组中无重复元素。

示例 1:

输入: [1,3,5,6], 5
输出: 2
示例 2:

输入: [1,3,5,6], 2
输出: 1
示例 3:

输入: [1,3,5,6], 7
输出: 4
示例 4:

输入: [1,3,5,6], 0
输出: 0



##### Solution:

```python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        if target in nums:
            return nums.index(target)
        else:
            nums.append(target)
            nums.sort()
            return nums.index(target)
            
        
```
sort之后找index，没用二分查找


![pic](https://ws3.sinaimg.cn/large/006tNc79gy1g1yvmfocegj30tw094wg0.jpg)

用二分法：

```
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        low = 0  # 设定最小值
        high = len(nums)  #设定初始最大值
        while low < high:   
            mid = low + (high -low)//2  #找到中间值
            if nums[mid] > target:
                high = mid   #如果中间值比target大，就把mid作为最大值
            elif nums[mid] < target:
                low = mid +1  #如果中间值比target小，就把mid作为最小值，
            else:
                return mid
        return low
```

![pic](https://ws1.sinaimg.cn/large/006tNc79gy1g1ywiwz9ljj30ug094q4e.jpg)
