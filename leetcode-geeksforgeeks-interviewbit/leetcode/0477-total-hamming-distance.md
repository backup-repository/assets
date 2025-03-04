---
title: 0477 Total Hamming Distance
summary: 0477 Total Hamming Distance LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "0477-total-hamming-distance LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0477 Total Hamming Distance - Solution Explained/problem-solving.webp
    alt: 0477 Total Hamming Distance
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/total-hamming-distance/">477. Total Hamming Distance</a></h2><h3>Medium</h3><hr><div><p>The <a href="https://en.wikipedia.org/wiki/Hamming_distance" target="_blank">Hamming distance</a> between two integers is the number of positions at which the corresponding bits are different.</p>

<p>Given an integer array <code>nums</code>, return <em>the sum of <strong>Hamming distances</strong> between all the pairs of the integers in</em> <code>nums</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [4,14,2]
<strong>Output:</strong> 6
<strong>Explanation:</strong> In binary representation, the 4 is 0100, 14 is 1110, and 2 is 0010 (just
showing the four bits relevant in this case).
The answer will be:
HammingDistance(4, 14) + HammingDistance(4, 2) + HammingDistance(14, 2) = 2 + 2 + 2 = 6.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [4,14,4]
<strong>Output:</strong> 4
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
	<li>The answer for the given input will fit in a <strong>32-bit</strong> integer.</li>
</ul>
</div>

---




```python
class Solution:
    def totalHammingDistance(self, nums: List[int]) -> int:
        res = 0
        for i in range(32):
            zero, one = 0, 0
            for num in nums:
                if num & (1<<i):
                    one += 1
                else: 
                    zero += 1
            res += zero * one
        
        return res
```
