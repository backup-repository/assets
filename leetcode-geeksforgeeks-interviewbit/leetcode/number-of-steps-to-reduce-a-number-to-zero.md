---
title: Number Of Steps To Reduce A Number To Zero
summary: Number Of Steps To Reduce A Number To Zero LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "number-of-steps-to-reduce-a-number-to-zero LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Number Of Steps To Reduce A Number To Zero - Solution Explained/problem-solving.webp
    alt: Number Of Steps To Reduce A Number To Zero
    hiddenInList: true
    hiddenInSingle: false
---


<h2>1342. Number of Steps to Reduce a Number to Zero</h2><h3>Easy</h3><hr><div><p>Given a non-negative integer <code>num</code>, return the number of steps to reduce it to zero. If the current number is even, you have to divide it by 2, otherwise, you have to subtract 1 from it.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> num = 14
<strong>Output:</strong> 6
<strong>Explanation:</strong>&nbsp;
Step 1) 14 is even; divide by 2 and obtain 7.&nbsp;
Step 2) 7 is odd; subtract 1 and obtain 6.
Step 3) 6 is even; divide by 2 and obtain 3.&nbsp;
Step 4) 3 is odd; subtract 1 and obtain 2.&nbsp;
Step 5) 2 is even; divide by 2 and obtain 1.&nbsp;
Step 6) 1 is odd; subtract 1 and obtain 0.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> num = 8
<strong>Output:</strong> 4
<strong>Explanation:</strong>&nbsp;
Step 1) 8 is even; divide by 2 and obtain 4.&nbsp;
Step 2) 4 is even; divide by 2 and obtain 2.&nbsp;
Step 3) 2 is even; divide by 2 and obtain 1.&nbsp;
Step 4) 1 is odd; subtract 1 and obtain 0.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> num = 123
<strong>Output:</strong> 12
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= num &lt;= 10^6</code></li>
</ul>
</div>

---




```cpp
class Solution {
public:
    int numberOfSteps (int num) {
        int ans=0;
        while(num!=0){
            if(num%2==0)
                num=num/2;
            else
                num--;
            ans++;
        }
        return ans;
    }
};
```
