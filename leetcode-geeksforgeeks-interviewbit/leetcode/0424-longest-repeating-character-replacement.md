---
title: 0424 Longest Repeating Character Replacement
summary: 0424 Longest Repeating Character Replacement LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "0424-longest-repeating-character-replacement LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0424 Longest Repeating Character Replacement - Solution Explained/problem-solving.webp
    alt: 0424 Longest Repeating Character Replacement
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/longest-repeating-character-replacement/">424. Longest Repeating Character Replacement</a></h2><h3>Medium</h3><hr><div><p>You are given a string <code>s</code> and an integer <code>k</code>. You can choose any character of the string and change it to any other uppercase English character. You can perform this operation at most <code>k</code> times.</p>

<p>Return <em>the length of the longest substring containing the same letter you can get after performing the above operations</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> s = "ABAB", k = 2
<strong>Output:</strong> 4
<strong>Explanation:</strong> Replace the two 'A's with two 'B's or vice versa.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> s = "AABABBA", k = 1
<strong>Output:</strong> 4
<strong>Explanation:</strong> Replace the one 'A' in the middle with 'B' and form "AABBBBA".
The substring "BBBB" has the longest repeating letters, which is 4.
There may exists other ways to achive this answer too.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> consists of only uppercase English letters.</li>
	<li><code>0 &lt;= k &lt;= s.length</code></li>
</ul>
</div>

---




```python
# https://leetcode.com/problems/longest-repeating-character-replacement/

'''Intuition:
- Scan the array with 2 pointers: left and right
- Store the frequency of each character
- Compute the replacement cost: cells count between left and right pointers - the highest frequency
- if the replacement cost <= k: update longest string size
- if the replacement cost > k: decrease frequency of character at left pointer; increase left pointer and repeat.
'''

class Solution:
    def characterReplacement(self, s, k):
        maxFreq = 1
        freq = collections.Counter()
        res = 1
        l = 0
        for r in range(len(s)):
            freq[s[r]] += 1
            maxFreq = max(maxFreq, freq[s[r]])
            cost = (r-l+1) - maxFreq
            if cost <= k:
                res = max(res, r-l+1)
            else:
                freq[s[l]] -= 1
                l += 1
        
        return res
    
    
    
# Time: O(N)
# Space: O(N)
```
