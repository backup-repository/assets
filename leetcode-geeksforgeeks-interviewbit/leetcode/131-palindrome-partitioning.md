---
title: 131 Palindrome Partitioning
summary: 131 Palindrome Partitioning LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "131-palindrome-partitioning LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:131 Palindrome Partitioning - Solution Explained/problem-solving.webp
    alt: 131 Palindrome Partitioning
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/palindrome-partitioning/">131. Palindrome Partitioning</a></h2><h3>Medium</h3><hr><div><p>Given a string <code>s</code>, partition <code>s</code> such that every substring of the partition is a <strong>palindrome</strong>. Return all possible palindrome partitioning of <code>s</code>.</p>

<p>A <strong>palindrome</strong> string is a string that reads the same backward as forward.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "aab"
<strong>Output:</strong> [["a","a","b"],["aa","b"]]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = "a"
<strong>Output:</strong> [["a"]]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 16</code></li>
	<li><code>s</code> contains only lowercase English letters.</li>
</ul>
</div>

---




```python
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        res = []
        
        def solve(s, path):
            if not s:
                res.append(path)
                return
            for i in range(1, len(s)+1):
                if s[:i] == s[:i][::-1]:
                    solve(s[i:], path + [s[:i]])
        
        solve(s, [])
        return res
```
