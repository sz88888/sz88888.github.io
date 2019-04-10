---
layout: post
title: "leetcode-11 Container With Most Water 盛最多水的容器"
subtitle: ""
date: 2019-03-09 21:32
author: "zsz"
catalog: true
tags: 
      - leetcode
      - python
      - algorithm

---





#### Container With Most Water

给定 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。

说明：你不能倾斜容器，且 n 的值至少为 2。

![pic](https://aliyun-lc-upload.oss-cn-hangzhou.aliyuncs.com/aliyun-lc-upload/uploads/2018/07/25/question_11.jpg)
图中垂直线代表输入数组 [1,8,6,2,5,4,8,3,7]。在此情况下，容器能够容纳水（表示为蓝色部分）的最大值为 49。

Example:
```
输入: [1,8,6,2,5,4,8,3,7]
输出: 49
```

##### Solution:

```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        left = 0                #最左边
        right = len(height) - 1 #最右边
        max = 0                 #初始面积为0
        while left < right:
            b = right - left
            if height[left] < height[right]:
                h = height[left]
                left += 1
            else:
                h = height[right]
                right -= 1
            area = b*h
            if max < area:
                max = area
        return max
        
```



