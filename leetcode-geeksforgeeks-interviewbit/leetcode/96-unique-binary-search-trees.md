---
title: 96 Unique Binary Search Trees
summary: 96 Unique Binary Search Trees LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "96-unique-binary-search-trees LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:96 Unique Binary Search Trees - Solution Explained/problem-solving.webp
    alt: 96 Unique Binary Search Trees
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/unique-binary-search-trees/">96. Unique Binary Search Trees</a></h2><h3>Medium</h3><hr><div><p>Given an integer <code>n</code>, return <em>the number of structurally unique <strong>BST'</strong>s (binary search trees) which has exactly </em><code>n</code><em> nodes of unique values from</em> <code>1</code> <em>to</em> <code>n</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/01/18/uniquebstn3.jpg" style="width: 600px; height: 148px;">
<pre><strong>Input:</strong> n = 3
<strong>Output:</strong> 5
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> n = 1
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 19</code></li>
</ul>
</div>

---




```python
# https://youtu.be/H1qjjkm3P3c
class Solution:
    def numTrees(self, n: int) -> int:
        '''
        # Recursive Solution 
        def solve(n):
            if n <= 1: return 1
            if n == 2: return 2
            if n == 3: return 5
            ans = 0
            for i in range(n):
                ans += solve(i) * solve(n-i-1)
            return ans
        
        return solve(n)
        '''
        # Dynamic Programming
        dp = [0] * (n+1)
        dp[0] = 1
        
        for i in range(1, n+1):
            for j in range(i):
                dp[i] += dp[j] * dp[i-j-1]
                
        return dp[-1]

# Time: O(n*n)
# Space: O(n)
```
