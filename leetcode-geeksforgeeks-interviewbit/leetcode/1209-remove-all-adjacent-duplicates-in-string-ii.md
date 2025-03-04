---
title: 1209 Remove All Adjacent Duplicates In String Ii
summary: 1209 Remove All Adjacent Duplicates In String Ii LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "1209-remove-all-adjacent-duplicates-in-string-ii LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1209 Remove All Adjacent Duplicates In String Ii - Solution Explained/problem-solving.webp
    alt: 1209 Remove All Adjacent Duplicates In String Ii
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string-ii/">1209. Remove All Adjacent Duplicates in String II</a></h2><h3>Medium</h3><hr><div><p>You are given a string <code>s</code> and an integer <code>k</code>, a <code>k</code> <strong>duplicate removal</strong> consists of choosing <code>k</code> adjacent and equal letters from <code>s</code> and removing them, causing the left and the right side of the deleted substring to concatenate together.</p>

<p>We repeatedly make <code>k</code> <strong>duplicate removals</strong> on <code>s</code> until we no longer can.</p>

<p>Return <em>the final string after all such duplicate removals have been made</em>. It is guaranteed that the answer is <strong>unique</strong>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> s = "abcd", k = 2
<strong>Output:</strong> "abcd"
<strong>Explanation: </strong>There's nothing to delete.</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> s = "deeedbbcccbdaa", k = 3
<strong>Output:</strong> "aa"
<strong>Explanation: 
</strong>First delete "eee" and "ccc", get "ddbbbdaa"
Then delete "bbb", get "dddaa"
Finally delete "ddd", get "aa"</pre>

<p><strong class="example">Example 3:</strong></p>

<pre><strong>Input:</strong> s = "pbbcggttciiippooaais", k = 2
<strong>Output:</strong> "ps"
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>2 &lt;= k &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> only contains lowercase English letters.</li>
</ul>
</div>

---




```python
# https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string-ii/

class Solution:
    def removeDuplicates(self, s: str, k: int) -> str:
        stack = [["#", 0]]
        for c in s:
            if stack[-1][0] == c:
                stack[-1][1] += 1
                if stack[-1][1] == k:
                    stack.pop()
            else:
                stack.append([c, 1])
                
        return "".join(c*cnt for c, cnt in stack)
    
# Time: O(N)
# Space: O(N)




'''
class Solution:
    def removeDuplicates(self, s: str, k: int) -> str:
        stack = []
        for i in s:
            if stack and stack[-1][1] == k:
                for _ in range(k):
                    stack.pop()
            if stack and stack[-1][0] == i:
                stack.append((i, stack[-1][1] + 1))
            else:
                stack.append((i, 1))
        
        if stack and stack[-1][1] == k:
            for _ in range(k):
                stack.pop()
        
        return "".join(c for c, i in stack)
'''
```
