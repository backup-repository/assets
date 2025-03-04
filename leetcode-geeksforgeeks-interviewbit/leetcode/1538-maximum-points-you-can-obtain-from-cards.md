---
title: 1538 Maximum Points You Can Obtain From Cards
summary: 1538 Maximum Points You Can Obtain From Cards LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "1538-maximum-points-you-can-obtain-from-cards LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1538 Maximum Points You Can Obtain From Cards - Solution Explained/problem-solving.webp
    alt: 1538 Maximum Points You Can Obtain From Cards
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards">1538. Maximum Points You Can Obtain from Cards</a></h2><h3>Medium</h3><hr><p>There are several cards <strong>arranged in a row</strong>, and each card has an associated number of points. The points are given in the integer array <code>cardPoints</code>.</p>

<p>In one step, you can take one card from the beginning or from the end of the row. You have to take exactly <code>k</code> cards.</p>

<p>Your score is the sum of the points of the cards you have taken.</p>

<p>Given the integer array <code>cardPoints</code> and the integer <code>k</code>, return the <em>maximum score</em> you can obtain.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> cardPoints = [1,2,3,4,5,6,1], k = 3
<strong>Output:</strong> 12
<strong>Explanation:</strong> After the first step, your score will always be 1. However, choosing the rightmost card first will maximize your total score. The optimal strategy is to take the three cards on the right, giving a final score of 1 + 6 + 5 = 12.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> cardPoints = [2,2,2], k = 2
<strong>Output:</strong> 4
<strong>Explanation:</strong> Regardless of which two cards you take, your score will always be 4.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> cardPoints = [9,7,7,9,7,7,9], k = 7
<strong>Output:</strong> 55
<strong>Explanation:</strong> You have to take all the cards. Your score is the sum of points of all cards.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= cardPoints.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= cardPoints[i] &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= k &lt;= cardPoints.length</code></li>
</ul>


---




```python
class Solution:
    def maxScore(self, cardPoints: List[int], k: int) -> int:
        n = len(cardPoints)
        # Find minimum sub array sum of length n-k
        prefixSum = []
        s = 0
        for i in cardPoints:
            prefixSum.append(s)
            s += i
        prefixSum.append(s)
        minSubArraySum = 2**31
        for i in range(n-k, n+1):
            minSubArraySum = min(minSubArraySum, prefixSum[i] - prefixSum[i-(n-k)])
        return sum(cardPoints) - minSubArraySum
```
