---
title: Verifying An Alien Dictionary
summary: Verifying An Alien Dictionary LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "verifying-an-alien-dictionary LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Verifying An Alien Dictionary - Solution Explained/problem-solving.webp
    alt: Verifying An Alien Dictionary
    hiddenInList: true
    hiddenInSingle: false
---


<h2>953. Verifying an Alien Dictionary</h2><h3>Easy</h3><hr><div><p>In an alien language, surprisingly they also use english lowercase letters, but possibly&nbsp;in a different <code>order</code>. The&nbsp;<code>order</code> of the alphabet&nbsp;is some permutation&nbsp;of lowercase letters.</p>

<p>Given a sequence of <code>words</code>&nbsp;written in the alien language,&nbsp;and the <code>order</code> of the alphabet,&nbsp;return <code>true</code> if and only if the given <code>words</code>&nbsp;are sorted lexicographicaly in this alien language.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> words = ["hello","leetcode"], order = "hlabcdefgijkmnopqrstuvwxyz"
<strong>Output:</strong> true
<strong>Explanation: </strong>As 'h' comes before 'l' in this language, then the sequence is sorted.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> words = ["word","world","row"], order = "worldabcefghijkmnpqstuvxyz"
<strong>Output:</strong> false
<strong>Explanation: </strong>As 'd' comes after 'l' in this language, then words[0] &gt; words[1], hence the sequence is unsorted.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> words = ["apple","app"], order = "abcdefghijklmnopqrstuvwxyz"
<strong>Output:</strong> false
<strong>Explanation: </strong>The first three characters "app" match, and the second string is shorter (in size.) According to lexicographical rules "apple" &gt; "app", because 'l' &gt; '∅', where '∅' is defined as the blank character which is less than any other character (<a href="https://en.wikipedia.org/wiki/Lexicographical_order" target="_blank">More info</a>).
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= words.length &lt;= 100</code></li>
	<li><code>1 &lt;= words[i].length &lt;= 20</code></li>
	<li><code>order.length == 26</code></li>
	<li>All characters in <code>words[i]</code> and <code>order</code> are English lowercase letters.</li>
</ul>
</div>

---




```cpp
class Solution {
public:
    bool isAlienSorted(vector<string>& words, string order) {
        int mapping[26];
        for (int i = 0; i < 26; i++)
            mapping[order[i] - 'a'] = i;
        for (string &w : words)
            for (char &c : w)
                c = mapping[c - 'a'];
        return is_sorted(words.begin(), words.end());
    }
};
```
