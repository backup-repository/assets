---
title: 1288 Remove Covered Intervals
summary: 1288 Remove Covered Intervals LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "1288-remove-covered-intervals LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1288 Remove Covered Intervals - Solution Explained/problem-solving.webp
    alt: 1288 Remove Covered Intervals
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/remove-covered-intervals/">1288. Remove Covered Intervals</a></h2><h3>Medium</h3><hr><div><p>Given an array <code>intervals</code> where <code>intervals[i] = [l<sub>i</sub>, r<sub>i</sub>]</code> represent the interval <code>[l<sub>i</sub>, r<sub>i</sub>)</code>, remove all intervals that are covered by another interval in the list.</p>

<p>The interval <code>[a, b)</code> is covered by the interval <code>[c, d)</code> if and only if <code>c &lt;= a</code> and <code>b &lt;= d</code>.</p>

<p>Return <em>the number of remaining intervals</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> intervals = [[1,4],[3,6],[2,8]]
<strong>Output:</strong> 2
<strong>Explanation:</strong> Interval [3,6] is covered by [2,8], therefore it is removed.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> intervals = [[1,4],[2,3]]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= intervals.length &lt;= 1000</code></li>
	<li><code>intervals[i].length == 2</code></li>
	<li><code>0 &lt;= l<sub>i</sub> &lt; r<sub>i</sub> &lt;= 10<sup>5</sup></code></li>
	<li>All the given intervals are <strong>unique</strong>.</li>
</ul>
</div>

---




```python
# https://leetcode.com/problems/remove-covered-intervals/

class Solution:
    def removeCoveredIntervals(self, intervals):
        intervals.sort(key = lambda x:(x[0], -x[1]))
        res = right = 0
        for l, r in intervals:
            res += r > right
            right = max(r, right)
        return res

# Time: O(N)
# Space: O(1)
    

'''
class Solution:
    def removeCoveredIntervals(self, intervals):
        intervals.sort(key = lambda x:(x[0], -x[1]), reverse = True)
        stack = []
        cnt = 0
        for l, r in intervals:
            while stack and l <= stack[-1][0] and stack[-1][1] <= r:
                stack.pop()
                cnt += 1
            stack.append((l,r))
        
        return len(intervals) - cnt
'''
```
