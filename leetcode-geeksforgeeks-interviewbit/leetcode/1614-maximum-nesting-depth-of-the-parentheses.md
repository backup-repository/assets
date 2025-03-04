---
title: 1614 Maximum Nesting Depth Of The Parentheses
summary: 1614 Maximum Nesting Depth Of The Parentheses LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "1614-maximum-nesting-depth-of-the-parentheses LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1614 Maximum Nesting Depth Of The Parentheses - Solution Explained/problem-solving.webp
    alt: 1614 Maximum Nesting Depth Of The Parentheses
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/maximum-nesting-depth-of-the-parentheses/">1614. Maximum Nesting Depth of the Parentheses</a></h2><h3>Easy</h3><hr><div><p>A string is a <strong>valid parentheses string</strong> (denoted <strong>VPS</strong>) if it meets one of the following:</p>

<ul>
	<li>It is an empty string <code>""</code>, or a single character not equal to <code>"("</code> or <code>")"</code>,</li>
	<li>It can be written as <code>AB</code> (<code>A</code> concatenated with <code>B</code>), where <code>A</code> and <code>B</code> are <strong>VPS</strong>'s, or</li>
	<li>It can be written as <code>(A)</code>, where <code>A</code> is a <strong>VPS</strong>.</li>
</ul>

<p>We can similarly define the <strong>nesting depth</strong> <code>depth(S)</code> of any VPS <code>S</code> as follows:</p>

<ul>
	<li><code>depth("") = 0</code></li>
	<li><code>depth(C) = 0</code>, where <code>C</code> is a string with a single character not equal to <code>"("</code> or <code>")"</code>.</li>
	<li><code>depth(A + B) = max(depth(A), depth(B))</code>, where <code>A</code> and <code>B</code> are <strong>VPS</strong>'s.</li>
	<li><code>depth("(" + A + ")") = 1 + depth(A)</code>, where <code>A</code> is a <strong>VPS</strong>.</li>
</ul>

<p>For example, <code>""</code>, <code>"()()"</code>, and <code>"()(()())"</code> are <strong>VPS</strong>'s (with nesting depths 0, 1, and 2), and <code>")("</code> and <code>"(()"</code> are not <strong>VPS</strong>'s.</p>

<p>Given a <strong>VPS</strong> represented as string <code>s</code>, return <em>the <strong>nesting depth</strong> of </em><code>s</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "(1+(2*3)+((<u>8</u>)/4))+1"
<strong>Output:</strong> 3
<strong>Explanation:</strong> Digit 8 is inside of 3 nested parentheses in the string.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "(1)+((2))+(((<u>3</u>)))"
<strong>Output:</strong> 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 100</code></li>
	<li><code>s</code> consists of digits <code>0-9</code> and characters <code>'+'</code>, <code>'-'</code>, <code>'*'</code>, <code>'/'</code>, <code>'('</code>, and <code>')'</code>.</li>
	<li>It is guaranteed that parentheses expression <code>s</code> is a <strong>VPS</strong>.</li>
</ul>
</div>

---




```python
class Solution:
    def maxDepth(self, s: str) -> int:
        res = 0
        count = 0
        
        for i in s:
            if i == "(":
                count += 1
            elif i == ")":
                count -= 1
            res = max(res, count)
        
        return res
```
