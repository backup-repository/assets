---
title: 516 Longest Palindromic Subsequence
summary: 516 Longest Palindromic Subsequence LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "516-longest-palindromic-subsequence LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:516 Longest Palindromic Subsequence - Solution Explained/problem-solving.webp
    alt: 516 Longest Palindromic Subsequence
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/longest-palindromic-subsequence/">516. Longest Palindromic Subsequence</a></h2><h3>Medium</h3><hr><div><p>Given a string <code>s</code>, find <em>the longest palindromic <strong>subsequence</strong>'s length in</em> <code>s</code>.</p>

<p>A <strong>subsequence</strong> is a sequence that can be derived from another sequence by deleting some or no elements without changing the order of the remaining elements.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "bbbab"
<strong>Output:</strong> 4
<strong>Explanation:</strong> One possible longest palindromic subsequence is "bbbb".
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "cbbd"
<strong>Output:</strong> 2
<strong>Explanation:</strong> One possible longest palindromic subsequence is "bb".
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 1000</code></li>
	<li><code>s</code> consists only of lowercase English letters.</li>
</ul>
</div>

---




```python
class Solution:
    def longestPalindromeSubseq(self, s: str) -> int:
        def lcs(x, y):
            dp = [[0]*(len(y)+1) for j in range(len(x)+1)]
            
            for i in range(1, len(x)+1):
                for j in range(1, len(y)+1):
                    if x[i-1] == y[j-1]:
                        dp[i][j] = 1 + dp[i-1][j-1]
                    else:
                        dp[i][j] = max(dp[i-1][j], dp[i][j-1])
            
            return dp[-1][-1]
        
        return lcs(s, s[::-1])
```
