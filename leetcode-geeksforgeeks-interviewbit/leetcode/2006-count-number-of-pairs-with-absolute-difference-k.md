---
title: 2006 Count Number Of Pairs With Absolute Difference K
summary: 2006 Count Number Of Pairs With Absolute Difference K LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "2006-count-number-of-pairs-with-absolute-difference-k LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2006 Count Number Of Pairs With Absolute Difference K - Solution Explained/problem-solving.webp
    alt: 2006 Count Number Of Pairs With Absolute Difference K
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/count-number-of-pairs-with-absolute-difference-k/">2006. Count Number of Pairs With Absolute Difference K</a></h2><h3>Easy</h3><hr><div><p>Given an integer array <code>nums</code> and an integer <code>k</code>, return <em>the number of pairs</em> <code>(i, j)</code> <em>where</em> <code>i &lt; j</code> <em>such that</em> <code>|nums[i] - nums[j]| == k</code>.</p>

<p>The value of <code>|x|</code> is defined as:</p>

<ul>
	<li><code>x</code> if <code>x &gt;= 0</code>.</li>
	<li><code>-x</code> if <code>x &lt; 0</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [1,2,2,1], k = 1
<strong>Output:</strong> 4
<strong>Explanation:</strong> The pairs with an absolute difference of 1 are:
- [<strong><u>1</u></strong>,<strong><u>2</u></strong>,2,1]
- [<strong><u>1</u></strong>,2,<strong><u>2</u></strong>,1]
- [1,<strong><u>2</u></strong>,2,<strong><u>1</u></strong>]
- [1,2,<strong><u>2</u></strong>,<strong><u>1</u></strong>]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [1,3], k = 3
<strong>Output:</strong> 0
<strong>Explanation:</strong> There are no pairs with an absolute difference of 3.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> nums = [3,2,1,5,4], k = 2
<strong>Output:</strong> 3
<b>Explanation:</b> The pairs with an absolute difference of 2 are:
- [<strong><u>3</u></strong>,2,<strong><u>1</u></strong>,5,4]
- [<strong><u>3</u></strong>,2,1,<strong><u>5</u></strong>,4]
- [3,<strong><u>2</u></strong>,1,5,<strong><u>4</u></strong>]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 200</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 100</code></li>
	<li><code>1 &lt;= k &lt;= 99</code></li>
</ul>
</div>

---




```python
class Solution:
    def countKDifference(self, nums: List[int], k: int) -> int:
        seen = {i:0 for i in range(min(nums)-k, max(nums)+k+1)}
        count = 0
        for i in nums:
            count += seen[i-k] + seen[i+k]
            seen[i] += 1
        
        return count
```
