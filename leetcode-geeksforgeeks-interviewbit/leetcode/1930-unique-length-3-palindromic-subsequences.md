---
title: 1930 Unique Length 3 Palindromic Subsequences
summary: 1930 Unique Length 3 Palindromic Subsequences LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "1930-unique-length-3-palindromic-subsequences LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1930 Unique Length 3 Palindromic Subsequences - Solution Explained/problem-solving.webp
    alt: 1930 Unique Length 3 Palindromic Subsequences
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/unique-length-3-palindromic-subsequences/">1930. Unique Length-3 Palindromic Subsequences</a></h2><h3>Medium</h3><hr><div><p>Given a string <code>s</code>, return <em>the number of <strong>unique palindromes of length three</strong> that are a <strong>subsequence</strong> of </em><code>s</code>.</p>

<p>Note that even if there are multiple ways to obtain the same subsequence, it is still only counted <strong>once</strong>.</p>

<p>A <strong>palindrome</strong> is a string that reads the same forwards and backwards.</p>

<p>A <strong>subsequence</strong> of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.</p>

<ul>
	<li>For example, <code>"ace"</code> is a subsequence of <code>"<u>a</u>b<u>c</u>d<u>e</u>"</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> s = "aabca"
<strong>Output:</strong> 3
<strong>Explanation:</strong> The 3 palindromic subsequences of length 3 are:
- "aba" (subsequence of "<u>a</u>a<u>b</u>c<u>a</u>")
- "aaa" (subsequence of "<u>aa</u>bc<u>a</u>")
- "aca" (subsequence of "<u>a</u>ab<u>ca</u>")
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> s = "adc"
<strong>Output:</strong> 0
<strong>Explanation:</strong> There are no palindromic subsequences of length 3 in "adc".
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre><strong>Input:</strong> s = "bbcbaba"
<strong>Output:</strong> 4
<strong>Explanation:</strong> The 4 palindromic subsequences of length 3 are:
- "bbb" (subsequence of "<u>bb</u>c<u>b</u>aba")
- "bcb" (subsequence of "<u>b</u>b<u>cb</u>aba")
- "bab" (subsequence of "<u>b</u>bcb<u>ab</u>a")
- "aba" (subsequence of "bbcb<u>aba</u>")
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> consists of only lowercase English letters.</li>
</ul>
</div>

---




```python
# https://leetcode.com/problems/unique-length-3-palindromic-subsequences/

'''
Just notice we need to return the count of distinct palindromes having length 3(point to be noticed).
Special thing about these odd length palindromes are that they have first and last character same 
so we only need to check how many unique characters are there between first and last character(this can be done using set)
'''

class Solution:
    def countPalindromicSubsequence(self, s):
        res = 0
        for c in string.ascii_lowercase:  # Time: O(26)
            l = s.find(c)   # first occurance  # Time: O(N)
            r = s.rfind(c)  # last occurance
            if l > -1:
                res += len(set(s[l+1:r]))  # count of unique element in middle
        
        return res
      
      
# Time: O(26*N)
# Space: O(26*N)


```
