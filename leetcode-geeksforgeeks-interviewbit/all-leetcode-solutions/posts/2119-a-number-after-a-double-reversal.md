---
title: 2119 A Number After A Double Reversal
summary: 2119 A Number After A Double Reversal LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "2119 A Number After A Double Reversal LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2119 A Number After A Double Reversal - Solution Explained/problem-solving.webp
    alt: 2119 A Number After A Double Reversal
    hiddenInList: true
    hiddenInSingle: false
---


# [2119. A Number After a Double Reversal](https://leetcode.com/problems/a-number-after-a-double-reversal)


## Description

<p><strong>Reversing</strong> an integer means to reverse all its digits.</p>

<ul>
	<li>For example, reversing <code>2021</code> gives <code>1202</code>. Reversing <code>12300</code> gives <code>321</code> as the <strong>leading zeros are not retained</strong>.</li>
</ul>

<p>Given an integer <code>num</code>, <strong>reverse</strong> <code>num</code> to get <code>reversed1</code>, <strong>then reverse</strong> <code>reversed1</code> to get <code>reversed2</code>. Return <code>true</code> <em>if</em> <code>reversed2</code> <em>equals</em> <code>num</code>. Otherwise return <code>false</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> num = 526
<strong>Output:</strong> true
<strong>Explanation:</strong> Reverse num to get 625, then reverse 625 to get 526, which equals num.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> num = 1800
<strong>Output:</strong> false
<strong>Explanation:</strong> Reverse num to get 81, then reverse 81 to get 18, which does not equal num.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> num = 0
<strong>Output:</strong> true
<strong>Explanation:</strong> Reverse num to get 0, then reverse 0 to get 0, which equals num.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= num &lt;= 10<sup>6</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def isSameAfterReversals(self, num: int) -> bool:
        return num == 0 or num % 10 != 0
```

```java
class Solution {
    public boolean isSameAfterReversals(int num) {
        return num == 0 || num % 10 != 0;
    }
}
```

```cpp
class Solution {
public:
    bool isSameAfterReversals(int num) {
        return num == 0 || num % 10 != 0;
    }
};
```

```go
func isSameAfterReversals(num int) bool {
	return num == 0 || num%10 != 0
}
```

<!-- tabs:end -->

<!-- end -->
