---
title: 0714 Best Time To Buy And Sell Stock With Transaction Fee
summary: 0714 Best Time To Buy And Sell Stock With Transaction Fee LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "0714-best-time-to-buy-and-sell-stock-with-transaction-fee LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0714 Best Time To Buy And Sell Stock With Transaction Fee - Solution Explained/problem-solving.webp
    alt: 0714 Best Time To Buy And Sell Stock With Transaction Fee
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/">714. Best Time to Buy and Sell Stock with Transaction Fee</a></h2><h3>Medium</h3><hr><div><p>You are given an array <code>prices</code> where <code>prices[i]</code> is the price of a given stock on the <code>i<sup>th</sup></code> day, and an integer <code>fee</code> representing a transaction fee.</p>

<p>Find the maximum profit you can achieve. You may complete as many transactions as you like, but you need to pay the transaction fee for each transaction.</p>

<p><strong>Note:</strong> You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> prices = [1,3,2,8,4,9], fee = 2
<strong>Output:</strong> 8
<strong>Explanation:</strong> The maximum profit can be achieved by:
- Buying at prices[0] = 1
- Selling at prices[3] = 8
- Buying at prices[4] = 4
- Selling at prices[5] = 9
The total profit is ((8 - 1) - 2) + ((9 - 4) - 2) = 8.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> prices = [1,3,7,5,10,3], fee = 3
<strong>Output:</strong> 6
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= prices.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= prices[i] &lt; 5 * 10<sup>4</sup></code></li>
	<li><code>0 &lt;= fee &lt; 5 * 10<sup>4</sup></code></li>
</ul>
</div>

---




```python
class Solution:
    def maxProfit(self, prices: List[int], fee: int) -> int:
        obsp, ossp = -prices[0], 0
        nbsp, nssp = 0, 0
        
        for p in prices:
            nbsp = max(obsp, ossp - p)
            nssp = max(ossp, obsp + p - fee)
            
            obsp = nbsp
            ossp = nssp
        
        return ossp
```
