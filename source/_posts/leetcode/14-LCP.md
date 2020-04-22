---
title: Longest Common Prefix（最长公共前缀）
date: 2019-04-23 10:52:49
tags:
  - leetcode
  - java
categories:
  - 啦啦蕾的学习笔记～
  - 算法
katex: true
---

**Description:**
Write a function to find the longest common prefix string amongst an array of strings.
If there is no common prefix, return an empty string "". [Do it now!](https://leetcode.com/problems/longest-common-prefix/)
<!--more-->

### 方法1：Vertical scanning（垂直扫描）
- 思想：同一列从上往下比较。
- 实现代码：
``` java
public String longestCommonPrefix(String[] strs) {
    if(strs.length == 0) return "";
    for(int i = 0; i < strs[0].length(); i++) {
        for(String s : strs) {
            if (i >= s.length() || s.charAt(i) != strs[0].charAt(i)) 
                return strs[0].substring(0, i);
        }
    }
    return strs[0];
}
```
- 时间复杂度：\\(O(S)\\)，S是所有字符串的总和。空间复杂度：\\(O(1)\\)

&nbsp;
### 方法2：Horizontal scanning（水平扫描）
- 思想：先找到 \\(S_1\\) 和 \\(S_2\\) 的最长共前缀 \\(LCP(S_1, S_2)\\)，再找到 \\(LCP(S_1, S_2)\\) 和 \\(S_3\\) 的最长公共前缀 \\(LCP(LCP(S_1, S_2), S_3)\\)，这样一直到\\(S_n\\)。
> \\(LCP(S_1, S_n) = LCP(LCP(LCP(S_1, S_2), S_3),...S_n)\\)
- 实现代码：
```java
  public String longestCommonPrefix(String[] strs) {
    if(strs.length == 0) return "";
    String prefix = strs[0];
    for(int i = 1; i < strs.length; i++) {
        while (strs[i].indexOf(prefix) != 0) {
            prefix = prefix.substring(0, prefix.length() - 1);
            if (prefix == "") return "";
        }
    }
    return prefix;
  }
```
- 时间复杂度：\\(O(S)\\)，S是所有字符串的总和。空间复杂度：\\(O(1)\\)

&nbsp;
### 方法3：Divide and conquer（分治法）
- 思想：由方法2的公式可以注意到 \\(LCP(S_1, S_n) = LCP(LCP(S_1...S_k), LCP(S_{k+1}...S_n))\\)，将 \\(LCP(S_1, S_n)\\) 问题划分为求2个子问题 \\(LCP(S_1, S_{mid})\\) 和 \\(LCP(S_{mid+1}...S_j)\\)，其中 \\(mid = \frac{i+j}{2}\\)。
- 实现代码：
```java
public String longestCommonPrefix(String[] strs) {
    if (strs.length == 0) return "";
    return longestCommonPrefix(strs, 0, strs.length - 1);
}
private String longestCommonPrefix(String[] strs, int l, int r){
    if (l == r) return strs[l];
    int mid = (l + r)/2;
    String lcpl = longestCommonPrefix(strs, l, mid);
    String lcpr = longestCommonPrefix(strs, mid+1, r);
    return commonPrefix(lcpl, lcpr);
}
String commonPrefix(String l, String r) {
    int min = Math.min(l.length(), r.length());
    for (int i = 0; i < min; i++) {
        if (l.charAt(i) != r.charAt(i)) return l.substring(0, i);
    }
    return l.substring(0, min);
}
```
- 时间复杂度：\\(O(S)\\)（官方给的），感觉不对，我觉得是 \\(O(m*logn)\\)。
- 空间复杂度：\\(O(m*logn)\\)，\\(n\\) 是字符串数，\\(m\\) 是字符串的长度。由于在堆栈中存储递归调用，有 \\(logn\\) 的递归调用，每个需要 \\(m\\) 的空间存储结果。

&nbsp;
### 方法4：Binary search（二分搜索法）
- 思想：算法的搜索空间是 \\((0...min\\_len)\\)，每一次将搜索空间划分成两部分，其中一部分在判断是否为公共前缀之后可以丢弃。有两种可能情况：
  1. \\(S[1...mid]\\) 是公共前缀，则这部分可以丢弃掉，继续往前寻找更长的部分。
  2. \\(S[1...mid]\\) 不是公共前缀，则 \\(S[mid+1...min\\_len]\\) 可以丢弃掉，因为它一定不是公共前缀。
- 实现代码：
```java
public String longestCommonPrefix(String[] strs) {
    if (strs.length == 0) return "";
    int min_len = strs[0].length();
    for(String s: strs) {
        min_len = Math.min(min_len, s.length());
    }
    int low = 1, high = min_len;
    while (low <= high) {
        int mid = (low + high) / 2;
        if (isCommonPrefix(strs, mid)) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    return strs[0].substring(0, (low+high)/2);
}
Boolean isCommonPrefix(String[] strs, int len) {
    String s0 = strs[0].substring(0, len);
    for (int i = 1; i < strs.length; i++) {
        if (!strs[i].startsWith(s0)) return false;
    }
    return true;
}
```
- 时间复杂度：\\(O(S*logm)\\)，空间复杂度：\\(O(1)\\)