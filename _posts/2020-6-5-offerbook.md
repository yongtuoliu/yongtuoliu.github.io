---
title: 'Offer Book'
date: 2012-08-14
permalink: /posts/2012/08/offerbook/
tags:
  - cool posts
  - plan
---

以下题目来自《剑指offer》& LeetCode

## 题目1：面试题59 - I. 滑动窗口的最大值
给定一个数组 nums 和滑动窗口的大小 k，请找出所有滑动窗口里的最大值。
```
输入: nums = [1,3,-1,-3,5,3,6,7], 和 k = 3
输出: [3,3,5,5,6,7] 
解释: 

  滑动窗口的位置                最大值
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7

```

***Answer:*** 使用一个队列来存储当前最大值，从后面开始只记录非严格递增的数，窗口滑动时遇到队列第一个数，就去掉。
```PY
class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        n = len(nums)
        if n==0 or n<k:
            return []
        queue = collections.deque([])
        for i in range(k):
            value = nums[i]
            while queue and queue[-1]<value:
                queue.pop()
            queue.append(value)
        res = []
        res.append(queue[0])
        for i in range(k,n):
            if queue[0] == nums[i-k]:
                queue.popleft()
            value = nums[i]
            while queue and queue[-1]<value:
                queue.pop()
            queue.append(value)
            res.append(queue[0])

        return res
```

## 题目2: 面试题64. 求1+2+…+n
要求不能使用乘除法、for、while、if、else、switch、case等关键字及条件判断语句（A?B:C）。
```py
输入: n = 3
输出: 6
```

***Answer:*** 利用bool操作的前判断性
```py
class Solution:
    def __init__(self):
        self.res = 0
    def sumNums(self, n: int) -> int:
        n > 1 and self.sumNums(n - 1)
        self.res += n
        return self.res
```

## 题目3：面试题38. 字符串的排列
输入一个字符串，打印出该字符串中字符的所有排列。
你可以以任意顺序返回这个字符串数组，但里面不能有重复元素。
```py
输入：s = "abc"
输出：["abc","acb","bac","bca","cab","cba"]
```
***Answer:*** dfs+剪枝
```py
class Solution:
    def permutation(self, s: str) -> List[str]:
        n = len(s)
        if n < 2:
            return [s]
        self.res = []
        def helper(current,rest):
            if len(rest) == 0:
                if not current in self.res:
                    self.res.append(current)
            else:
                record = []
                for i in range(len(rest)):
                    if rest[i] in record:
                        continue
                    helper(current+rest[i],rest[:i]+rest[(i+1):])
                    record.append(rest[i])
        helper('',s)
        return self.res
```

## 题目4：单词搜索 II
给定一个二维网格 board 和一个字典中的单词列表 words，找出所有同时在二维网格和字典中出现的单词。
单词必须按照字母顺序，通过相邻的单元格内的字母构成，其中“相邻”单元格是那些水平相邻或垂直相邻的单元格。同一个单元格内的字母在一个单词中不允许被重复使用。
```py
输入: 
words = ["oath","pea","eat","rain"] and board =
[
  ['o','a','a','n'],
  ['e','t','a','e'],
  ['i','h','k','r'],
  ['i','f','l','v']
]

输出: ["eat","oath"]
```


