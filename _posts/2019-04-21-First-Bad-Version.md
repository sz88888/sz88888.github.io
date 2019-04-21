---
layout: post
title: "leetcode-278 First Bad Version 第一个错误的版本"
subtitle: ""
date: 2019-04-11 21:32
author: "zsz"
catalog: true
tags: 
      - leetcode
      - python
      - algorithm
      - Binary Search 二分查找

---





#### First Bad Version

你是产品经理，目前正在带领一个团队开发新的产品。不幸的是，你的产品的最新版本没有通过质量检测。由于每个版本都是基于之前的版本开发的，所以错误的版本之后的所有版本都是错的。

假设你有 n 个版本 [1, 2, ..., n]，你想找出导致之后所有版本出错的第一个错误的版本。

你可以通过调用 bool isBadVersion(version) 接口来判断版本号 version 是否在单元测试中出错。实现一个函数来查找第一个错误的版本。你应该尽量减少对调用 API 的次数。

示例:

给定 n = 5，并且 version = 4 是第一个错误的版本。

调用 isBadVersion(3) -> false
调用 isBadVersion(5) -> true
调用 isBadVersion(4) -> true

所以，4 是第一个错误的版本。 



##### Solution:

```python
# The isBadVersion API is already defined for you.
# @param version, an integer
# @return a bool
# def isBadVersion(version):

class Solution:
    def firstBadVersion(self, n):
        """
        :type n: int
        :rtype: int
        """
        low = 1
        high = int(n)
        while low<high:
            mid = low + (high-low)/2
            if isBadVersion(mid):
                high = mid
            else:
                low = mid + 1
        return int(low)
                

                
```



![pic](https://ws2.sinaimg.cn/large/006tNc79gy1g2aov5zj7hj30u8088ta4.jpg)

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
