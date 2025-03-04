---
title: 322 Coin Change
summary: 322 Coin Change LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "322-coin-change LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:322 Coin Change - Solution Explained/problem-solving.webp
    alt: 322 Coin Change
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/coin-change/">322. Coin Change</a></h2><h3>Medium</h3><hr><div><p>You are given an integer array <code>coins</code> representing coins of different denominations and an integer <code>amount</code> representing a total amount of money.</p>

<p>Return <em>the fewest number of coins that you need to make up that amount</em>. If that amount of money cannot be made up by any combination of the coins, return <code>-1</code>.</p>

<p>You may assume that you have an infinite number of each kind of coin.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> coins = [1,2,5], amount = 11
<strong>Output:</strong> 3
<strong>Explanation:</strong> 11 = 5 + 5 + 1
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> coins = [2], amount = 3
<strong>Output:</strong> -1
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> coins = [1], amount = 0
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= coins.length &lt;= 12</code></li>
	<li><code>1 &lt;= coins[i] &lt;= 2<sup>31</sup> - 1</code></li>
	<li><code>0 &lt;= amount &lt;= 10<sup>4</sup></code></li>
</ul>
</div>

---




```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        dp = [[2**31]*(amount+1) for _ in range(len(coins)+1)]
        for i in range(len(coins)+1):
            dp[i][0] = 0
        
        for j in range(1, amount+1):
            if j % coins[0] == 0:
                dp[1][j] = j // coins[0]
        
        for i in range(2, len(coins)+1):
            for j in range(1, amount+1):
                if coins[i-1] <= j:
                    dp[i][j] = min(1 + dp[i][j - coins[i-1]], dp[i-1][j])
                else:
                    dp[i][j] = dp[i-1][j]
        
        return dp[-1][-1] if dp[-1][-1] != 2**31 else -1
```
