---
title: 1884 Egg Drop With 2 Eggs And N Floors
summary: 1884 Egg Drop With 2 Eggs And N Floors LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "1884-egg-drop-with-2-eggs-and-n-floors LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1884 Egg Drop With 2 Eggs And N Floors - Solution Explained/problem-solving.webp
    alt: 1884 Egg Drop With 2 Eggs And N Floors
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/egg-drop-with-2-eggs-and-n-floors/">1884. Egg Drop With 2 Eggs and N Floors</a></h2><h3>Medium</h3><hr><div><p>You are given <strong>two identical</strong> eggs and you have access to a building with <code>n</code> floors labeled from <code>1</code> to <code>n</code>.</p>

<p>You know that there exists a floor <code>f</code> where <code>0 &lt;= f &lt;= n</code> such that any egg dropped at a floor <strong>higher</strong> than <code>f</code> will <strong>break</strong>, and any egg dropped <strong>at or below</strong> floor <code>f</code> will <strong>not break</strong>.</p>

<p>In each move, you may take an <strong>unbroken</strong> egg and drop it from any floor <code>x</code> (where <code>1 &lt;= x &lt;= n</code>). If the egg breaks, you can no longer use it. However, if the egg does not break, you may <strong>reuse</strong> it in future moves.</p>

<p>Return <em>the <strong>minimum number of moves</strong> that you need to determine <strong>with certainty</strong> what the value of </em><code>f</code> is.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> n = 2
<strong>Output:</strong> 2
<strong>Explanation:</strong> We can drop the first egg from floor 1 and the second egg from floor 2.
If the first egg breaks, we know that f = 0.
If the second egg breaks but the first egg didn't, we know that f = 1.
Otherwise, if both eggs survive, we know that f = 2.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> n = 100
<strong>Output:</strong> 14
<strong>Explanation:</strong> One optimal strategy is:
- Drop the 1st egg at floor 9. If it breaks, we know f is between 0 and 8. Drop the 2nd egg starting from floor 1 and going up one at a time to find f within 8 more drops. Total drops is 1 + 8 = 9.
- If the 1st egg does not break, drop the 1st egg again at floor 22. If it breaks, we know f is between 9 and 21. Drop the 2nd egg starting from floor 10 and going up one at a time to find f within 12 more drops. Total drops is 2 + 12 = 14.
- If the 1st egg does not break again, follow a similar process dropping the 1st egg from floors 34, 45, 55, 64, 72, 79, 85, 90, 94, 97, 99, and 100.
Regardless of the outcome, it takes at most 14 drops to determine f.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 1000</code></li>
</ul>
</div>

---




```python
class Solution:
    def twoEggDrop(self, n: int) -> int:
        dp = [[-1]*5 for i in range(n+5)]
        
        def solve(e, n):
            if n == 0 or n == 1: return n
            if e == 1: return n
            
            if dp[n][e] != -1: return dp[n][e]
            
            ans = 2**31
            for f in range(1, n+1):
                tmp = 1 + max(solve(e-1, f-1), solve(e, n-f))
                ans = min(ans, tmp)
            dp[n][e] = ans
            return dp[n][e]
        
        return solve(2, n)
```
