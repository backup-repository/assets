---
title: Sum Of Two Integers
summary: Sum Of Two Integers LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "sum-of-two-integers LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Sum Of Two Integers - Solution Explained/problem-solving.webp
    alt: Sum Of Two Integers
    hiddenInList: true
    hiddenInSingle: false
---


<h2>371. Sum of Two Integers</h2><h3>Medium</h3><hr><div><p>Calculate the sum of two integers <i>a</i> and <i>b</i>, but you are <b>not allowed</b> to use the operator <code>+</code> and <code>-</code>.</p>

<div>
<p><strong>Example 1:</strong></p>

<pre><strong>Input: </strong>a = <span id="example-input-1-1">1</span>, b = <span id="example-input-1-2">2</span>
<strong>Output: </strong><span id="example-output-1">3</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre><strong>Input: </strong>a = -<span id="example-input-2-1">2</span>, b = <span id="example-input-2-2">3</span>
<strong>Output: </strong>1
</pre>
</div>
</div>
</div>

---




```cpp
class Solution {
public:
    int getSum(int a, int b) {
        unsigned int carry=a&b;
        unsigned int sum=a^b;
        if(carry==0)
            return sum;
        carry<<=1;
        return getSum(sum, carry);
    }
};
```
