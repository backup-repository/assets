---
title: 1461 Check If A String Contains All Binary Codes Of Size K
summary: 1461 Check If A String Contains All Binary Codes Of Size K LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "1461-check-if-a-string-contains-all-binary-codes-of-size-k LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1461 Check If A String Contains All Binary Codes Of Size K - Solution Explained/problem-solving.webp
    alt: 1461 Check If A String Contains All Binary Codes Of Size K
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/check-if-a-string-contains-all-binary-codes-of-size-k/">1461. Check If a String Contains All Binary Codes of Size K</a></h2><h3>Medium</h3><hr><div><p>Given a binary string <code>s</code> and an integer <code>k</code>, return <code>true</code> <em>if every binary code of length</em> <code>k</code> <em>is a substring of</em> <code>s</code>. Otherwise, return <code>false</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> s = "00110110", k = 2
<strong>Output:</strong> true
<strong>Explanation:</strong> The binary codes of length 2 are "00", "01", "10" and "11". They can be all found as substrings at indices 0, 1, 3 and 2 respectively.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> s = "0110", k = 1
<strong>Output:</strong> true
<strong>Explanation:</strong> The binary codes of length 1 are "0" and "1", it is clear that both exist as a substring. 
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre><strong>Input:</strong> s = "0110", k = 2
<strong>Output:</strong> false
<strong>Explanation:</strong> The binary code "00" is of length 2 and does not exist in the array.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 5 * 10<sup>5</sup></code></li>
	<li><code>s[i]</code> is either <code>'0'</code> or <code>'1'</code>.</li>
	<li><code>1 &lt;= k &lt;= 20</code></li>
</ul>
</div>

---




```python
class Solution:
    def hasAllCodes(self, s: str, k: int) -> bool:
        unique = set()
        for i in range(k-1, len(s)):
            sb = s[i-k+1:i+1]
            unique.add(sb)
        return len(unique) == 2**k
```
