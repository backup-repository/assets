---
title: 394 Decode String
summary: 394 Decode String LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "394-decode-string LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:394 Decode String - Solution Explained/problem-solving.webp
    alt: 394 Decode String
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/decode-string/">394. Decode String</a></h2><h3>Medium</h3><hr><div><p>Given an encoded string, return its decoded string.</p>

<p>The encoding rule is: <code>k[encoded_string]</code>, where the <code>encoded_string</code> inside the square brackets is being repeated exactly <code>k</code> times. Note that <code>k</code> is guaranteed to be a positive integer.</p>

<p>You may assume that the input string is always valid; there are no extra white spaces, square brackets are well-formed, etc.</p>

<p>Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers, <code>k</code>. For example, there will not be input like <code>3a</code> or <code>2[4]</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "3[a]2[bc]"
<strong>Output:</strong> "aaabcbc"
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "3[a2[c]]"
<strong>Output:</strong> "accaccacc"
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> s = "2[abc]3[cd]ef"
<strong>Output:</strong> "abcabccdcdcdef"
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 30</code></li>
	<li><code>s</code> consists of lowercase English letters, digits, and square brackets <code>'[]'</code>.</li>
	<li><code>s</code> is guaranteed to be <strong>a valid</strong> input.</li>
	<li>All the integers in <code>s</code> are in the range <code>[1, 300]</code>.</li>
</ul>
</div>

---




```python
# https://leetcode.com/problems/decode-string/

class Solution:
    def decodeString(self, s: str) -> str:
        stack = []; curNum = 0; curString = ''
        
        for ch in s:
            if ch.isdigit():
                curNum = curNum * 10 + int(ch)
            
            elif ch == '[':
                stack.append(curString)
                stack.append(curNum)
                curNum = 0
                curString = ''
            
            elif ch == ']':
                num = stack.pop()
                prevString = stack.pop()
                curString = prevString + num * curString
                
            else:
                curString += ch
        
        return curString
    
# Time: O(N)
# Space: O(N)
```
