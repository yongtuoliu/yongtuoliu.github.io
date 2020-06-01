---
title: '算法刷题：矩阵系列'
date: 2020-6-01
permalink: /posts/201/08/matrix/
tags:
  - matrix
  - algorithm
---

以下题目均来自LeetCode。


## 题目1： 01 矩阵
给定一个由 0 和 1 组成的矩阵，找出每个元素到最近的 0 的距离。
两个相邻元素间的距离为 1 。

```py
输入:
0 0 0
0 1 0
0 0 0
输出:
0 0 0
0 1 0
0 0 0
```
***Answer:***
思路：采用宽度优先搜索：
```py
class Solution:
    def updateMatrix(self, matrix: List[List[int]]) -> List[List[int]]:
        n = len(matrix)
        if n==0:
            return []
        m = len(matrix[0])
        if m==0:
            return [[] for _ in range(n)]
        res = [[m+n]*m for i in range(n)]
        queue = collections.deque([])
        flag = [[-1]*m for i in range(n)]
        moves = [[-1,0],[1,0],[0,1],[0,-1]]
        for i in range(n):
            for j in range(m):
                if matrix[i][j] == 0:
                    queue.append([i,j,0])
                    flag[i][j]=1
                    res[i][j] = 0
        iterator = 0
        while len(queue)>0:
            iterator+=1
            k  = len(queue)
            for i in range(k):
                x,y,value = queue.popleft()
                for mv in moves:
                    if x+mv[0]>=0 and x+mv[0]<n and y+mv[1]>=0 and y+mv[1]<m and flag[x+mv[0]][y+mv[1]] == -1:
                        res[x+mv[0]][y+mv[1]] = value+1
                        queue.append([x+mv[0],y+mv[1],res[x+mv[0]][y+mv[1]]])
                        flag[x+mv[0]][y+mv[1]]=1
        return res
```

## 题目2：排序矩阵查找
给定M×N矩阵，每一行、每一列都按升序排列，请编写代码找出某元素。

```py
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
给定 target = 5，返回 true。
给定 target = 20，返回 false。
```

***Answer:***
思路：类似二分法：
```py
class Solution:
    def searchMatrix(self, matrix, target: int) -> bool:
        n = len(matrix)
        if n==0:
            return False
        m = len(matrix[0])
        if m==0:
            return False
        row = 0
        columns = m-1
        while columns!=-1 and row!=n:
            if matrix[row][columns]>target:
                columns-=1
            elif matrix[row][columns]<target:
                row+=1
            else:
                return True
        return False
```