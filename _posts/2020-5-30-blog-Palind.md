---
title: '算法刷题：回文串系列'
date: 2020-5-30
permalink: /posts/2020/05/palind/
tags:
  - cool posts
  - plan
---

## 题目1：最长回文子串
给定一个字符串 s，找到 s 中最长的回文子串。你可以假设 s 的最大长度为 1000。

```py
输入: "babad"
输出: "bab"
注意: "aba" 也是一个有效答案。

输入: "cbbd"
输出: "bb"
```

***Answer:***
-   思路：回文串一般采用动态规划算法。
-   对于一个子串而言，如果它是回文串，并且长度大于2，那么将它首尾的两个字母去除之后，它仍然是个回文串。
-   建立数组P[i,j]表示str[i:j] 为回文串
-   状态转移方程 $P[i,j] = P[i+1，j-1] \&\& (str[i] == str[j])$
-   确定初状态P[0,0]=True
-   遍历从第i个下标开始，长为j的回文串是否存在

```py
class Solution:
    def longestPalindrome(self, s: str) -> str:
        if len(s) == 0:
            return s
        dp = [[False]*len(s) for _ in range(len(s))]
        dp[0][0]=True
        ans = ""
        for l in range(len(s)):
            for i in range(len(s)):
                end = l+i
                if end>=len(s):
                    break
                if end == i:
                    dp[i][end] = True
                elif l == 1:
                    dp[i][end] = (s[i]==s[end])
                else:
                    dp[i][end] = (dp[i + 1][end - 1] and s[i] == s[end])
                if dp[i][end] and len(s[i:end+1])>len(ans):
                    ans = s[i:end+1]
        return ans
```

## 题目2：分割回文串
给定一个字符串 s，将 s 分割成一些子串，使每个子串都是回文串。
返回 s 所有可能的分割方案。
```py
输入: "aab"
输出:
[
  ["aa","b"],
  ["a","a","b"]
]
```
***Answer:***
思路1：使用回溯法,相当于$dp[i,k] = \sum dp[i,j]+str[j:k]$，其中str[j:k]是回文串
```py
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        res = []
        def forward(string,subresult):
            if not string:
                res.append(subresult)
            for i in range(1,len(string)+1):
                if string[:i] == string[:i][::-1]:
                    helper(string[i:],subresult+[string[:i]])
        helper(s,[])
        return res
```
思路2：联系上一题，先确定dp[i,j]是否是回文串，再DFS遍历所有可能的路径，也就是dp[0,i]+dp[i,j]+dp[j,k]+dp[k,n],这解法转载自powcai
```py
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        result= []
        n = len(s)
        dp = [[False]*n for _ in range(n)]
        dp[0][0] = True
        for i in range(n):
            for j in range(i+1):
                if s[i] == s[j] and (i-j<=2 or dp[j+1][i-1]==True):
                    dp[j][i] = True
        def recall(idx,subresult):
            if idx==n:
                result.append(subresult)
            for i in range(idx,n):
                if dp[idx][i]:
                    recall(i+1,subresult+[s[idx:i+1]])
        recall(0,[])
        return result
```
## 题目3：回文子串
给定一个字符串，你的任务是计算这个字符串中有多少个回文子串。
具有不同开始位置或结束位置的子串，即使是由相同的字符组成，也会被计为是不同的子串。
```py
输入: "aaa"
输出: 6
说明: 6个回文子串: "a", "a", "a", "aa", "aa", "aaa".
```
***Answer:*** 
思路1：如题目2，采用动态规划
```py
class Solution:
    def countSubstrings(self, s: str) -> int:
        count = 0
        n = len(s)
        dp = [[False]*n for _ in range(n)]
        for i in range(n):
            for j in range(i+1):
                if s[i] == s[j] and (i-j<=2 or dp[j+1][i-1]):
                    dp[j][i]=True
                    count+=1
        return count
```
## 题目4： 验证回文串
给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。
说明：本题中，我们将空字符串定义为有效的回文串。
```py
输入: "A man, a plan, a canal: Panama"
输出: true
```
***Answer:***
思路：清除无效字符
```py
class Solution:
    def isPalindrome(self, s: str) -> bool:
        if len(s) == 0:
            return True
        s = s.lower()
        def Valid(char):
            if (char>='0' and char<='9') or (char>='a' and char<='z') or(char>='A' and char<='Z'):
                return True
            return False
        string = []
        for char in s:
            if Valid(char):
                string.append(char)
        string = ''.join(string)
        if string == string[::-1]:
            return True
        return False
```

## 题目5： 破坏回文串
给你一个回文字符串 palindrome ，请你将其中 一个 字符用任意小写英文字母替换，使得结果字符串的字典序最小，且 不是 回文串。
请你返回结果字符串。如果无法做到，则返回一个空串。
```py
输入：palindrome = "abccba"
输出："aaccba"
输入：palindrome = "a"
输出：""
```
***Answer:***
思路：字典序最小，也就是要填充尽可能小的字符,比如ab>aa，所以要尽可往前填a，当遇到所有都是a时，要在最后一位填b。
由于是回文串，所以前一半和后一半是相同的，我们只要遍历前一半就好，如果前一半都是a,那么后一半也全是a,所以要修改回文串且字典序最小，则在最后一位将a变为b
```py
class Solution:
    def breakPalindrome(self, palindrome: str) -> str:
        n = len(palindrome)
        if n<2:
            return ""
        for i in range(int(n/2)):
            if palindrome[i]!='a':
                return palindrome[:i]+'a'+palindrome[i+1:]
        return palindrome[:n-1]+'b'
```
