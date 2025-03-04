---
title: Construct K Palindrome Strings
summary: Construct K Palindrome Strings LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "construct-k-palindrome-strings LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Construct K Palindrome Strings - Solution Explained/problem-solving.webp
    alt: Construct K Palindrome Strings
    hiddenInList: true
    hiddenInSingle: false
---


[Discussion Post (created on 16/1/2021 at 16:44)](https://leetcode.com/problems/construct-k-palindrome-strings/discuss/1068238/C%2B%2B-or-Beats-99.8)  
<h2>1400. Construct K Palindrome Strings</h2><h3>Medium</h3><hr><div><p>Given a string <code>s</code> and an integer <code>k</code>. You should construct <code>k</code> non-empty <strong>palindrome</strong> strings using <strong>all the characters</strong> in <code>s</code>.</p>

<p>Return <em><strong>True</strong></em> if you can use all the characters in <code>s</code> to construct <code>k</code> palindrome strings or <em><strong>False</strong></em> otherwise.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "annabelle", k = 2
<strong>Output:</strong> true
<strong>Explanation:</strong> You can construct two palindromes using all characters in s.
Some possible constructions "anna" + "elble", "anbna" + "elle", "anellena" + "b"
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "leetcode", k = 3
<strong>Output:</strong> false
<strong>Explanation:</strong> It is impossible to construct 3 palindromes using all the characters of s.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> s = "true", k = 4
<strong>Output:</strong> true
<strong>Explanation:</strong> The only possible solution is to put each character in a separate string.
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> s = "yzyzyzyzyzyzyzy", k = 2
<strong>Output:</strong> true
<strong>Explanation:</strong> Simply you can put all z's in one string and all y's in the other string. Both strings will be palindrome.
</pre>

<p><strong>Example 5:</strong></p>

<pre><strong>Input:</strong> s = "cr", k = 7
<strong>Output:</strong> false
<strong>Explanation:</strong> We don't have enough characters in s to construct 7 palindromes.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10^5</code></li>
	<li>All characters in <code>s</code> are lower-case English letters.</li>
	<li><code>1 &lt;= k &lt;= 10^5</code></li>
</ul></div>

---




```cpp
class Solution {
public:
    bool canConstruct(string s, int k) {
        int n=s.size();
        if(n==k)
            return true;
        if(n<k)
            return false;
        int odd=0;
        int a[26]={0};
        for(int i=0;i<n;i++)
            a[s[i]-'a']++;
        for(int i=0;i<26;i++)
            if(a[i]%2!=0)
                odd++;
        return odd<=k && k<=n;
    }
};
```
