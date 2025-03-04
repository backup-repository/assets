---
title: 0812 Largest Triangle Area
summary: 0812 Largest Triangle Area LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "0812-largest-triangle-area LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0812 Largest Triangle Area - Solution Explained/problem-solving.webp
    alt: 0812 Largest Triangle Area
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/largest-triangle-area/">812. Largest Triangle Area</a></h2><h3>Easy</h3><hr><div><p>Given an array of points on the <strong>X-Y</strong> plane <code>points</code> where <code>points[i] = [x<sub>i</sub>, y<sub>i</sub>]</code>, return <em>the area of the largest triangle that can be formed by any three different points</em>. Answers within <code>10<sup>-5</sup></code> of the actual answer will be accepted.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://s3-lc-upload.s3.amazonaws.com/uploads/2018/04/04/1027.png" style="height: 369px; width: 450px;">
<pre><strong>Input:</strong> points = [[0,0],[0,1],[1,0],[0,2],[2,0]]
<strong>Output:</strong> 2.00000
<strong>Explanation:</strong> The five points are shown in the above figure. The red triangle is the largest.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> points = [[1,0],[0,0],[0,1]]
<strong>Output:</strong> 0.50000
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= points.length &lt;= 50</code></li>
	<li><code>-50 &lt;= x<sub>i</sub>, y<sub>i</sub> &lt;= 50</code></li>
	<li>All the given points are <strong>unique</strong>.</li>
</ul>
</div>

---




```python
# https://www.vedantu.com/question-answer/find-the-area-of-the-triangle-whose-vertices-are-class-11-maths-cbse-5f8309d2ed668270c0bf8f07

class Solution:
    def largestTriangleArea(self, points: List[List[int]]) -> float:
        n = len(points)
        res = 0
        for i in range(n-2):
            for j in range(i+1, n-1):
                for k in range(j+1, n):
                    x1, y1 = points[i]
                    x2, y2 = points[j]
                    x3, y3 = points[k]
                    area = abs(0.5 * (x1*(y2-y3) + x2*(y3-y1) + x3*(y1-y2)))
                    res = max(res, area)
        
        return res
```
