---
title: 0123 Best Time To Buy And Sell Stock Iii
summary: 0123 Best Time To Buy And Sell Stock Iii LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "0123-best-time-to-buy-and-sell-stock-iii LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0123 Best Time To Buy And Sell Stock Iii - Solution Explained/problem-solving.webp
    alt: 0123 Best Time To Buy And Sell Stock Iii
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/">123. Best Time to Buy and Sell Stock III</a></h2><h3>Hard</h3><hr><div><p>You are given an array <code>prices</code> where <code>prices[i]</code> is the price of a given stock on the <code>i<sup>th</sup></code> day.</p>

<p>Find the maximum profit you can achieve. You may complete <strong>at most two transactions</strong>.</p>

<p><strong>Note:</strong> You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> prices = [3,3,5,0,0,3,1,4]
<strong>Output:</strong> 6
<strong>Explanation:</strong> Buy on day 4 (price = 0) and sell on day 6 (price = 3), profit = 3-0 = 3.
Then buy on day 7 (price = 1) and sell on day 8 (price = 4), profit = 4-1 = 3.</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> prices = [1,2,3,4,5]
<strong>Output:</strong> 4
<strong>Explanation:</strong> Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are engaging multiple transactions at the same time. You must sell before buying again.
</pre>

<p><strong class="example">Example 3:</strong></p>

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
        profit_left = [0]*len(prices)
        minsofar = prices[0]
        maxprofit = 0
        for i, p in enumerate(prices):
            maxprofit = max(maxprofit, p - minsofar)
            minsofar = min(minsofar, p)
            profit_left[i] = maxprofit
        
        profit_right = [0]*len(prices)
        maxsofar = prices[-1]
        maxprofit = 0
        for i in range(len(prices)-1, -1, -1):
            p = prices[i]
            maxprofit = max(maxprofit, maxsofar - p)
            maxsofar = max(maxsofar, p)
            profit_right[i] = maxprofit
        
        res = 0
        for pl, pr in zip(profit_left, profit_right):
            res = max(res, pl+pr)
        # print(profit_left)
        # print(profit_right)
        return res
```
