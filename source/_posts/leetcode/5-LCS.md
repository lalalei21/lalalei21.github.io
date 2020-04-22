---
title: Longest Palindromic Substring (最长回文子串)
date: 2019-04-19 13:04:58
tags:
  - leetcode
  - java
categories:
  - 啦啦蕾的学习笔记～
  - 算法
katex: true
---
**Description:**
Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000. [Do it now!](https://leetcode.com/problems/longest-palindromic-substring/)

<!--more-->

### 方案1: Longest Common Substring（类似于求最长公共子串问题）
- [最长公共子串参考文档](https://www.kancloud.cn/digest/pieces-algorithm/163624)
- 想法：S‘为S的转置，求S和S’的最长公共子串
	> 例子：S = "c**aba**", S'= "**aba**c".  -> SS = "aba"

- 产生的错误：
	> 例子：S = "**aacd**fg**dcaa**", S'= "**aacd**gf**dcaa**". 即当S的其它部分出现非回文子串的转置时，会产生错误，此时输出 SS = "abcad"

- 解决方案：增加判断条件，候选子串的索引必须与其转置的索引相同
  \\( i + j + 2 - a[i][j] == len \\)

- 实现代码：
```java
  public String longestPalindrome(String s) {    
    if(s.length() <= 1) return s;
    if(s.length() == 2) return s.charAt(0) == s.charAt(1) ? s : s.substring(0, 1);
    int max_i = 0, max_len = 0;
    int len = s.length();
    int[][] a = new int[len][len];
    for(int i = 0; i < len; i++) {
        a[i][0] = s.charAt(len - 1) == s.charAt(i) ? 1 : 0;
    }
    for(int i = 0; i < len; i++) {
        a[0][i] = s.charAt(0) == s.charAt(len - i - 1) ? 1 : 0;
    }
    for(int i = 1; i < len; i++) {
        for(int j = 1; j < len; j++) {
            if (s.charAt(i) == s.charAt(len-j-1)) {
                a[i][j] = a[i-1][j-1] + 1;
                if (i + j + 2 - a[i][j] == len && a[i][j] > max_len) {
                  max_i = i;
                  max_len = a[i][j];
                }
            } else {
                a[i][j] = 0;
            }
        }
    }
    return s.substring(max_i - max_len + 1, max_i + 1);
  }
```
- 时间复杂度：\\(O(n^2)\\)，空间复杂度：\\(O(n^2)\\)

&nbsp;
### 方案2: Brute Force（暴力解法）
- 想法：很明显，就是枚举全部可能的子串，验证它是否为回文串。
- 时间复杂度：\\(O(n^3)\\)
  > 假设 \\(n\\) = 输入串的长度，那么它的子串数为 \\(\frac{n*(n-1)}{2}\\)，每一次验证需要 \\(O(n)\\) 时间
- 空间复杂度：\\(O(1)\\)


&nbsp;
### 方案3: Dynamic Programming（动态规划）
- 想法：为了改进暴力解法，我们需要观察如何在验证回文数时避免不必要的重复计算。
> 例子："bab"是回文数，那么只要首位字母相等，那么"babab"一定也是。
<div>$$
define P(i, j)=
\begin{cases}
true,&\text{if the substring is a palindrome}\\false,&\text{otherwise}
\end{cases}
$$</div>

  则，\\( P(i, j) = (P(i+1, j-1) \\; and \\; S_i = S_j) \\) 
  初始化为，\\( P(i, i) = true\\)，\\( P(i, i+1) = (S_i = S_{i+1}) \\)
- 代码实现：
```java
  public String longestPalindrome(String s) {
    if(s.length() <= 1) return s;
    int max_i = 0, max_j = 0;
    int len = s.length();
    boolean[][] a = new boolean[len][len];
    a[len-1][len-1] = true;
    for(int i = len-2; i >= 0; i--) {
        a[i][i] = true;
        for(int j = i+1; j < len; j++) {
            a[i][j] = s.charAt(i) == s.charAt(j) && (j==i+1 || a[i+1][j-1]);
            if(a[i][j] && j - i > max_j - max_i) {
                max_j = j;
                max_i = i;
            }
        }
    }
    return s.substring(max_i, max_j + 1);
  }
```
- 时间复杂度：\\(O(n^2)\\)，空间复杂度：\\(O(n^2)\\)

&nbsp;
### 方案4: Expand Around Center（中心扩展法）
- 想法：每个回文串都有一个中心，一个长度为 $n$ 的字符串可能的中心点有 $2n-1$ 个。通过中心向两边扩展，验证扩展的字符串是否为回文。
> 例子："aba"的中心是"b"，"abba"的中心是2个b之间。则字符串的可能中心数 = n(字符数) + (n-1)(字符间的空位数)
- 实现代码：
```java
public String longestPalindrome(String s) {
    if(s.length() <= 1) return s;
    int max_i = 0, max_j = 0;
    for (int i = 0; i < s.length(); i++) {
        int len1 = expandAroundCenter(s, i, i);
        int len2 = expandAroundCenter(s, i, i+1);
        int len = len1 > len2 ? len1 : len2;
        if(len > max_j - max_i) {
            max_i = i - (len-1)/2;
            max_j = max_i + len;
        }
    }
    return s.substring(max_i, max_j);
}
int expandAroundCenter(String s, int l, int r) {
    while (l >= 0 && r < s.length() && s.charAt(l) == s.charAt(r)) {
        l--;
        r++;
    }
    return r - l - 1;
}
```
- 时间复杂度：\\(O(n^2)\\)，空间复杂度：\\(O(1)\\)

&nbsp;
### 方案5: Manacher's Algorithm（马拉车算法）
- [算法思想 - 这篇介绍的很详细](https://blog.csdn.net/liuwei0604/article/details/50414542)，在线性时间复杂度内求出一个字符串的最长回文字串
- 实现代码：
```java
public String longestPalindrome(String s) {
    char[] T = new char[s.length()*2 + 1];
    int[] Len = new int[T.length];
    // p0表示最长回文子串的中心位索引，p表示最长回文子串的最远字符索引
    int p0 = 0, p = 0;
    // aaaba -> #a#a#a#b#a
    // 由于除了空字符以外的在s中也可能会出现，在这里不进行赋值默认为空字符，但是注释中为了方便会用#代替空字符
    for(int i = 0; i < s.length(); i++){
        T[2*i+1] = s.charAt(i);
    }
    // 0索引处永远为'#'
    Len[0] = 1;
    for(int i = 1; i < T.length; i++){
        // 算法的核心步骤
        Len[i] = i < p ? Math.min(Len[2*p0 - i], p-i+1) : 1;
        while(i-Len[i] >= 0 && i+Len[i] < T.length && T[i-Len[i]] == T[i+Len[i]]) {
            Len[i]++;
        }
        // 这里用 > 代替 >= 会节省算法时间
        if (Len[i] > p-p0+1) {
            p0 = i;
            p = i + Len[i] - 1;
        }
    }
    return s.substring((2*p0-p)/2, p/2);
}
```
- 时间复杂度：\\(O(n)\\)，空间复杂度：\\(O(n)\\)