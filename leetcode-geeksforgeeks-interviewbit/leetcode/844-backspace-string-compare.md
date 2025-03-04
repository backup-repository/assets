---
title: 844 Backspace String Compare
summary: 844 Backspace String Compare LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "844-backspace-string-compare LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:844 Backspace String Compare - Solution Explained/problem-solving.webp
    alt: 844 Backspace String Compare
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/backspace-string-compare/">844. Backspace String Compare</a></h2><h3>Easy</h3><hr><div><p>Given two strings <code>s</code> and <code>t</code>, return <code>true</code> <em>if they are equal when both are typed into empty text editors</em>. <code>'#'</code> means a backspace character.</p>

<p>Note that after backspacing an empty text, the text will continue empty.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "ab#c", t = "ad#c"
<strong>Output:</strong> true
<strong>Explanation:</strong> Both s and t become "ac".
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "ab##", t = "c#d#"
<strong>Output:</strong> true
<strong>Explanation:</strong> Both s and t become "".
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> s = "a#c", t = "b"
<strong>Output:</strong> false
<strong>Explanation:</strong> s becomes "c" while t becomes "b".
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code><span>1 &lt;= s.length, t.length &lt;= 200</span></code></li>
	<li><span><code>s</code> and <code>t</code> only contain lowercase letters and <code>'#'</code> characters.</span></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> Can you solve it in <code>O(n)</code> time and <code>O(1)</code> space?</p>
</div>

---




```python
class Solution:
    def backspaceCompare(self, s: str, t: str) -> bool:
        i = len(s) - 1  # Traverse from the end of the strings
        j = len(t) - 1 
        # The number of backspaces required till we arrive at a valid character
        bs = 0  # count of backspace for s
        bt = 0  # count of backspace for t
        
        while i >= 0 or j >= 0:
            while i >= 0:  # count bs
                if s[i] == "#":
                    bs += 1
                    i -= 1
                elif bs > 0 and s[i] != "#":
                    bs -= 1
                    i -= 1
                else:
                    break
                    
            while j >= 0:  # count bt
                if t[j] == "#":
                    bt += 1
                    j -= 1
                elif bt > 0 and t[j] != "#":
                    bt -= 1
                    j -= 1
                else:
                    break
            # Also ensure that both the character indices are valid. If it is not valid,  it means that we are comparing a "#" with a valid character.
            if i >= 0 and j < 0: return False
            if i < 0 and j >= 0: return False
            
            if s[i] != t[j]: return False
            
            i -= 1
            j -= 1
        
        
        return True
```
