---
title: Power Of Three
summary: Power Of Three LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "power-of-three LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Power Of Three - Solution Explained/problem-solving.webp
    alt: Power Of Three
    hiddenInList: true
    hiddenInSingle: false
---


<h2>326. Power of Three</h2><h3>Easy</h3><hr><div><p>Given an integer <code>n</code>, return <em><code>true</code> if it is a power of three. Otherwise, return <code>false</code></em>.</p>

<p>An integer <code>n</code> is a power of three, if there exists an integer <code>x</code> such that <code>n == 3<sup>x</sup></code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> n = 27
<strong>Output:</strong> true
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> n = 0
<strong>Output:</strong> false
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> n = 9
<strong>Output:</strong> true
</pre><p><strong>Example 4:</strong></p>
<pre><strong>Input:</strong> n = 45
<strong>Output:</strong> false
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-2<sup>31</sup> &lt;= n &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

<p>&nbsp;</p>
<strong>Follow up:</strong> Could you solve it without loops/recursion?</div>

---




```cpp
class Solution {
public:
    bool isPowerOfThree(int n) {
        int k=2;
        int r=0;
        if(n<1)
            return false;
        if(n==1)
            return true;
        while(n>1){
            r=n%3;
            if(r!=0)
                return false;
            n/=3;
        }
        return true;
    }
};
```
