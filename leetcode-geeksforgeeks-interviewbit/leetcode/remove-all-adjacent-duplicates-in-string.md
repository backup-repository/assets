---
title: Remove All Adjacent Duplicates In String
summary: Remove All Adjacent Duplicates In String LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "remove-all-adjacent-duplicates-in-string LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Remove All Adjacent Duplicates In String - Solution Explained/problem-solving.webp
    alt: Remove All Adjacent Duplicates In String
    hiddenInList: true
    hiddenInSingle: false
---


<h2>1047. Remove All Adjacent Duplicates In String</h2><h3>Easy</h3><hr><div><p>You are given a string <code>s</code> consisting of lowercase English letters. A <strong>duplicate removal</strong> consists of choosing two <strong>adjacent</strong> and <strong>equal</strong> letters and removing them.</p>

<p>We repeatedly make <strong>duplicate removals</strong> on <code>s</code> until we no longer can.</p>

<p>Return <em>the final string after all such duplicate removals have been made</em>. It can be proven that the answer is <strong>unique</strong>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "abbaca"
<strong>Output:</strong> "ca"
<strong>Explanation:</strong> 
For example, in "abbaca" we could remove "bb" since the letters are adjacent and equal, and this is the only possible move.  The result of this move is that the string is "aaca", of which only "aa" is possible, so the final string is "ca".
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "azxxzy"
<strong>Output:</strong> "ay"
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> consists of lowercase English letters.</li>
</ul>
</div>

---




```cpp
class Solution {
public:
    // use string as stack
    string removeDuplicates(string s) {
        string st;
        for(int i=0;i<s.size();i++){
            if(st.empty())
                st.push_back(s[i]);
            else{
                if(st.back()==s[i])
                    st.pop_back();
                else
                    st.push_back(s[i]);
            }
        }
        return st;
    }
};
```
