---
title: Longest Substring Without Repeating Characters
summary: Longest Substring Without Repeating Characters LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "longest-substring-without-repeating-characters LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Longest Substring Without Repeating Characters - Solution Explained/problem-solving.webp
    alt: Longest Substring Without Repeating Characters
    hiddenInList: true
    hiddenInSingle: false
---


<h2>3. Longest Substring Without Repeating Characters</h2><h3>Medium</h3><hr><div><p>Given a string <code>s</code>, find the length of the <b>longest substring</b> without repeating characters.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "abcabcbb"
<strong>Output:</strong> 3
<strong>Explanation:</strong> The answer is "abc", with the length of 3.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "bbbbb"
<strong>Output:</strong> 1
<strong>Explanation:</strong> The answer is "b", with the length of 1.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> s = "pwwkew"
<strong>Output:</strong> 3
<strong>Explanation:</strong> The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> s = ""
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= s.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>s</code> consists of English letters, digits, symbols and spaces.</li>
</ul>
</div>

---




```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int i=0,j=0;
	    int n=s.size();
	    map<char, int> m;
	    int ans=0;
	    while(j<n){
	        m[s[j]]++;
	        if(m.size()>j-i+1)
	        j++;
	        else if(m.size()==j-i+1){
	            ans=max(ans,j-i+1);
	            j++;
	        }
	        else{
	            while(m.size()<j-i+1){
	                m[s[i]]--;
	                if(m[s[i]]==0)
	                  m.erase(s[i]);
	                i++;
	            }
	            j++;
	        }
	    }
	    
	    return ans;
	    
    }
};
```
