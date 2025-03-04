---
title: 1673 Find The Most Competitive Subsequence
summary: 1673 Find The Most Competitive Subsequence LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "1673-find-the-most-competitive-subsequence LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1673 Find The Most Competitive Subsequence - Solution Explained/problem-solving.webp
    alt: 1673 Find The Most Competitive Subsequence
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/find-the-most-competitive-subsequence/">1673. Find the Most Competitive Subsequence</a></h2><h3>Medium</h3><hr><div><p>Given an integer array <code>nums</code> and a positive integer <code>k</code>, return <em>the most<strong> competitive</strong> subsequence of </em><code>nums</code> <em>of size </em><code>k</code>.</p>

<p>An array's subsequence is a resulting sequence obtained by erasing some (possibly zero) elements from the array.</p>

<p>We define that a subsequence <code>a</code> is more <strong>competitive</strong> than a subsequence <code>b</code> (of the same length) if in the first position where <code>a</code> and <code>b</code> differ, subsequence <code>a</code> has a number <strong>less</strong> than the corresponding number in <code>b</code>. For example, <code>[1,3,4]</code> is more competitive than <code>[1,3,5]</code> because the first position they differ is at the final number, and <code>4</code> is less than <code>5</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [3,5,2,6], k = 2
<strong>Output:</strong> [2,6]
<strong>Explanation:</strong> Among the set of every possible subsequence: {[3,5], [3,2], [3,6], [5,2], [5,6], [2,6]}, [2,6] is the most competitive.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [2,4,3,3,5,4,9,6], k = 4
<strong>Output:</strong> [2,3,3,4]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
	<li><code>1 &lt;= k &lt;= nums.length</code></li>
</ul>
</div>

---




```python
class Solution:
    def mostCompetitive(self, nums: List[int], k: int) -> List[int]:
        n = len(nums)
        stack = []
        for i, ch in enumerate(nums):
            rem = n - (i+1)
            while stack and stack[-1] > ch and rem >= k - len(stack):
                stack.pop()
            stack.append(ch)
        
        return stack[:k]
        
```
