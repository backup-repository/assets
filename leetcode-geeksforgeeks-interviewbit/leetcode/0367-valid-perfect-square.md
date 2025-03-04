---
title: 0367 Valid Perfect Square
summary: 0367 Valid Perfect Square LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "0367-valid-perfect-square LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0367 Valid Perfect Square - Solution Explained/problem-solving.webp
    alt: 0367 Valid Perfect Square
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/valid-perfect-square/">367. Valid Perfect Square</a></h2><h3>Easy</h3><hr><div><p>Given a positive integer num, return <code>true</code> <em>if</em> <code>num</code> <em>is a perfect square or</em> <code>false</code> <em>otherwise</em>.</p>

<p>A <strong>perfect square</strong> is an integer that is the square of an integer. In other words, it is the product of some integer with itself.</p>

<p>You must not use any built-in library function, such as <code>sqrt</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> num = 16
<strong>Output:</strong> true
<strong>Explanation:</strong> We return true because 4 * 4 = 16 and 4 is an integer.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> num = 14
<strong>Output:</strong> false
<strong>Explanation:</strong> We return false because 3.742 * 3.742 = 14 and 3.742 is not an integer.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= num &lt;= 2<sup>31</sup> - 1</code></li>
</ul>
</div>

---




```python
class Solution:
    def isPerfectSquare(self, num: int) -> bool:
        l = 0; r = num
        while l <= r:
            m = l + (r-l)//2
            if m*m < num:
                l = m + 1
            elif m*m > num:
                r = m - 1
            else:
                return True
        
        return False
```
