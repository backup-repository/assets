---
title: 0781 Rabbits In Forest
summary: 0781 Rabbits In Forest LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "0781-rabbits-in-forest LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0781 Rabbits In Forest - Solution Explained/problem-solving.webp
    alt: 0781 Rabbits In Forest
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/rabbits-in-forest/">781. Rabbits in Forest</a></h2><h3>Medium</h3><hr><div><p>There is a forest with an unknown number of rabbits. We asked n rabbits <strong>"How many rabbits have the same color as you?"</strong> and collected the answers in an integer array <code>answers</code> where <code>answers[i]</code> is the answer of the <code>i<sup>th</sup></code> rabbit.</p>

<p>Given the array <code>answers</code>, return <em>the minimum number of rabbits that could be in the forest</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> answers = [1,1,2]
<strong>Output:</strong> 5
<strong>Explanation:</strong>
The two rabbits that answered "1" could both be the same color, say red.
The rabbit that answered "2" can't be red or the answers would be inconsistent.
Say the rabbit that answered "2" was blue.
Then there should be 2 other blue rabbits in the forest that didn't answer into the array.
The smallest possible number of rabbits in the forest is therefore 5: 3 that answered plus 2 that didn't.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> answers = [10,10,10]
<strong>Output:</strong> 11
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= answers.length &lt;= 1000</code></li>
	<li><code>0 &lt;= answers[i] &lt; 1000</code></li>
</ul>
</div>

---




```python
class Solution:
    def numRabbits(self, answers: List[int]) -> int:
        cnt = collections.Counter()
        for i in answers:
            cnt[i] += 1
        
        res = 0
        for i in cnt:
            c = cnt[i]
            res += ceil(c/(i+1)) * (i+1)
        
        return res
```
