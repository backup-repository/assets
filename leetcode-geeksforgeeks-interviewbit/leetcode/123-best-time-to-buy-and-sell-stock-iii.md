---
title: 123 Best Time To Buy And Sell Stock Iii
summary: 123 Best Time To Buy And Sell Stock Iii LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "123-best-time-to-buy-and-sell-stock-iii LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:123 Best Time To Buy And Sell Stock Iii - Solution Explained/problem-solving.webp
    alt: 123 Best Time To Buy And Sell Stock Iii
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/">123. Best Time to Buy and Sell Stock III</a></h2><h3>Hard</h3><hr><div><p>You are given an array <code>prices</code> where <code>prices[i]</code> is the price of a given stock on the <code>i<sup>th</sup></code> day.</p>

<p>Find the maximum profit you can achieve. You may complete <strong>at most two transactions</strong>.</p>

<p><strong>Note:</strong> You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> prices = [3,3,5,0,0,3,1,4]
<strong>Output:</strong> 6
<strong>Explanation:</strong> Buy on day 4 (price = 0) and sell on day 6 (price = 3), profit = 3-0 = 3.
Then buy on day 7 (price = 1) and sell on day 8 (price = 4), profit = 4-1 = 3.</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> prices = [1,2,3,4,5]
<strong>Output:</strong> 4
<strong>Explanation:</strong> Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are engaging multiple transactions at the same time. You must sell before buying again.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> prices = [7,6,4,3,1]
<strong>Output:</strong> 0
<strong>Explanation:</strong> In this case, no transaction is done, i.e. max profit = 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= prices.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= prices[i] &lt;= 10<sup>5</sup></code></li>
</ul>
</div>

---




```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        n = len(prices)
        
        mini = prices[0]
        tmpres = 0
        profit1 = [0]*n
        for i in range(n):
            mini = min(mini, prices[i])
            tmpres = max(tmpres, prices[i] - mini)
            profit1[i] = tmpres
        
        maxi = prices[n-1]
        tmpres = 0
        profit2 = [0]*n
        for i in range(n-1, -1, -1):
            maxi = max(maxi, prices[i])
            tmpres = max(tmpres, maxi - prices[i])
            profit2[i] = tmpres
        
        res = 0
        for i in range(n):
            res = max(res, profit1[i] + profit2[i])
        
        print(profit1)
        print(profit2)
        return res
```
