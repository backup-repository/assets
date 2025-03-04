---
title: 198 House Robber
summary: 198 House Robber LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "198-house-robber LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:198 House Robber - Solution Explained/problem-solving.webp
    alt: 198 House Robber
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/house-robber/">198. House Robber</a></h2><h3>Medium</h3><hr><div><p>You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and <b>it will automatically contact the police if two adjacent houses were broken into on the same night</b>.</p>

<p>Given an integer array <code>nums</code> representing the amount of money of each house, return <em>the maximum amount of money you can rob tonight <b>without alerting the police</b></em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [1,2,3,1]
<strong>Output:</strong> 4
<strong>Explanation:</strong> Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [2,7,9,3,1]
<strong>Output:</strong> 12
<strong>Explanation:</strong> Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
Total amount you can rob = 2 + 9 + 1 = 12.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 100</code></li>
	<li><code>0 &lt;= nums[i] &lt;= 400</code></li>
</ul>
</div>

---




```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        '''
        # Recursive Solution
        self.res = 0
        
        def solve(nums, path):
            if not nums:
                self.res = max(self.res, path)
                return
            for i in range(len(nums)):
                solve(nums[i+2:], path + nums[i])
            
        solve(nums, 0)
        return self.res
        '''
    
        # Dynamic Programming Solution
        n = len(nums)
        dp = [0] * (n+1)
        dp[1] = nums[0]
        
        for i in range(2, n+1):
            dp[i] = max(dp[i-1], nums[i-1] + dp[i-2])
            
        return dp[-1]
    
        # Time Complexity = O(n)
        # Space Complexity = O(n)
```
