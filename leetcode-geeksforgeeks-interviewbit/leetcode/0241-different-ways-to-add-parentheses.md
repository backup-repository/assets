---
title: 0241 Different Ways To Add Parentheses
summary: 0241 Different Ways To Add Parentheses LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "0241-different-ways-to-add-parentheses LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0241 Different Ways To Add Parentheses - Solution Explained/problem-solving.webp
    alt: 0241 Different Ways To Add Parentheses
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/different-ways-to-add-parentheses/">241. Different Ways to Add Parentheses</a></h2><h3>Medium</h3><hr><div><p>Given a string <code>expression</code> of numbers and operators, return <em>all possible results from computing all the different possible ways to group numbers and operators</em>. You may return the answer in <strong>any order</strong>.</p>

<p>The test cases are generated such that the output values fit in a 32-bit integer and the number of different results does not exceed <code>10<sup>4</sup></code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> expression = "2-1-1"
<strong>Output:</strong> [0,2]
<strong>Explanation:</strong>
((2-1)-1) = 0 
(2-(1-1)) = 2
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> expression = "2*3-4*5"
<strong>Output:</strong> [-34,-14,-10,-10,10]
<strong>Explanation:</strong>
(2*(3-(4*5))) = -34 
((2*3)-(4*5)) = -14 
((2*(3-4))*5) = -10 
(2*((3-4)*5)) = -10 
(((2*3)-4)*5) = 10
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= expression.length &lt;= 20</code></li>
	<li><code>expression</code> consists of digits and the operator <code>'+'</code>, <code>'-'</code>, and <code>'*'</code>.</li>
	<li>All the integer values in the input expression are in the range <code>[0, 99]</code>.</li>
</ul>
</div>

---




```python
class Solution:
    def diffWaysToCompute(self, s: str) -> List[int]:
        dp = {}
        
        def cal(sign, left, right):
            if sign == '+': return left + right
            elif sign == '-': return left - right
            else: return left * right
        
        def solve(s):
            if s.isdigit(): return [int(s)]
            if s in dp: return dp[s]
            ans = []
            for i in range(len(s)):
                if s[i] in "+-*":
                    for left in solve(s[:i]):
                        for right in solve(s[i+1:]):
                            ans.append(cal(s[i], left, right))
            dp[s] = ans
            return ans
        
        return solve(s)
```
