---
title: 1480 Running Sum Of 1D Array
summary: 1480 Running Sum Of 1D Array LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "1480-running-sum-of-1d-array LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1480 Running Sum Of 1D Array - Solution Explained/problem-solving.webp
    alt: 1480 Running Sum Of 1D Array
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/running-sum-of-1d-array/">1480. Running Sum of 1d Array</a></h2><h3>Easy</h3><hr><div><p>Given an array <code>nums</code>. We define a running sum of an array as&nbsp;<code>runningSum[i] = sum(nums[0]…nums[i])</code>.</p>

<p>Return the running sum of <code>nums</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [1,2,3,4]
<strong>Output:</strong> [1,3,6,10]
<strong>Explanation:</strong> Running sum is obtained as follows: [1, 1+2, 1+2+3, 1+2+3+4].</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [1,1,1,1,1]
<strong>Output:</strong> [1,2,3,4,5]
<strong>Explanation:</strong> Running sum is obtained as follows: [1, 1+1, 1+1+1, 1+1+1+1, 1+1+1+1+1].</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> nums = [3,1,2,10,1]
<strong>Output:</strong> [3,4,6,16,17]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 1000</code></li>
	<li><code>-10^6&nbsp;&lt;= nums[i] &lt;=&nbsp;10^6</code></li>
</ul></div>

---




```python
class Solution:
    def runningSum(self, nums: List[int]) -> List[int]:
        runningSum = []
        Sum = 0
        for  i in range(len(nums)):
            Sum += nums[i]
            runningSum.append(Sum)
        return runningSum
            
```
