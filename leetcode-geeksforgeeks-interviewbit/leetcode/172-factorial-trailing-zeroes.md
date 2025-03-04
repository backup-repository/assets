---
title: 172 Factorial Trailing Zeroes
summary: 172 Factorial Trailing Zeroes LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "172-factorial-trailing-zeroes LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:172 Factorial Trailing Zeroes - Solution Explained/problem-solving.webp
    alt: 172 Factorial Trailing Zeroes
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/factorial-trailing-zeroes/">172. Factorial Trailing Zeroes</a></h2><h3>Medium</h3><hr><div><p>Given an integer <code>n</code>, return <em>the number of trailing zeroes in </em><code>n!</code>.</p>

<p>Note that <code>n! = n * (n - 1) * (n - 2) * ... * 3 * 2 * 1</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> n = 3
<strong>Output:</strong> 0
<strong>Explanation:</strong> 3! = 6, no trailing zero.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> n = 5
<strong>Output:</strong> 1
<strong>Explanation:</strong> 5! = 120, one trailing zero.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> n = 0
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= n &lt;= 10<sup>4</sup></code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> Could you write a solution that works in logarithmic time complexity?</p>
</div>

---




```python
class Solution:
    def trailingZeroes(self, n: int) -> int:
        res = 0
        
        while n > 0:
            n = n// 5
            res += n
        
        return res
```
