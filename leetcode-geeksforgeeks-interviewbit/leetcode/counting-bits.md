---
title: Counting Bits
summary: Counting Bits LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "counting-bits LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Counting Bits - Solution Explained/problem-solving.webp
    alt: Counting Bits
    hiddenInList: true
    hiddenInSingle: false
---


<h2>338. Counting Bits</h2><h3>Medium</h3><hr><div><p>Given an integer <code>num</code>, return <em>an array of the number of</em> <code>1</code><em>'s in the binary representation of every number in the range</em> <code>[0, num]</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> num = 2
<strong>Output:</strong> [0,1,1]
<strong>Explanation:</strong>
0 --&gt; 0
1 --&gt; 1
2 --&gt; 10
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> num = 5
<strong>Output:</strong> [0,1,1,2,1,2]
<strong>Explanation:</strong>
0 --&gt; 0
1 --&gt; 1
2 --&gt; 10
3 --&gt; 11
4 --&gt; 100
5 --&gt; 101
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= num &lt;= 10<sup>5</sup></code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong></p>

<ul>
	<li>It is very easy to come up with a solution with run time <code>O(32n)</code>. Can you do it in linear time <code>O(n)</code> and possibly in a single pass?</li>
	<li>Could you solve it in <code>O(n)</code> space complexity?</li>
	<li>Can you do it without using any built-in function (i.e., like <code>__builtin_popcount</code> in C++)?</li>
</ul>
</div>

---




```cpp
class Solution {
public:
    vector<int> countBits(int num) {
        vector<int> t(num+1);
        if(num==0)
            return {0};
        t[0]=0;
        t[1]=1;
        for(int i=2;i<=num;i++){
            if(i%2==0)
                t[i]=t[i/2];
            else
                t[i]=t[i/2]+1;
        }
        return t;
    }
};
```
