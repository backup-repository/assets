---
title: 1009 Complement Of Base 10 Integer
summary: 1009 Complement Of Base 10 Integer LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1009 Complement Of Base 10 Integer LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1009 Complement Of Base 10 Integer - Solution Explained/problem-solving.webp
    alt: 1009 Complement Of Base 10 Integer
    hiddenInList: true
    hiddenInSingle: false
---


# [1009. Complement of Base 10 Integer](https://leetcode.com/problems/complement-of-base-10-integer)


## Description

<p>The <strong>complement</strong> of an integer is the integer you get when you flip all the <code>0</code>&#39;s to <code>1</code>&#39;s and all the <code>1</code>&#39;s to <code>0</code>&#39;s in its binary representation.</p>

<ul>
	<li>For example, The integer <code>5</code> is <code>&quot;101&quot;</code> in binary and its <strong>complement</strong> is <code>&quot;010&quot;</code> which is the integer <code>2</code>.</li>
</ul>

<p>Given an integer <code>n</code>, return <em>its complement</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 5
<strong>Output:</strong> 2
<strong>Explanation:</strong> 5 is &quot;101&quot; in binary, with complement &quot;010&quot; in binary, which is 2 in base-10.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 7
<strong>Output:</strong> 0
<strong>Explanation:</strong> 7 is &quot;111&quot; in binary, with complement &quot;000&quot; in binary, which is 0 in base-10.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 10
<strong>Output:</strong> 5
<strong>Explanation:</strong> 10 is &quot;1010&quot; in binary, with complement &quot;0101&quot; in binary, which is 5 in base-10.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= n &lt; 10<sup>9</sup></code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Note:</strong> This question is the same as 476: <a href="https://leetcode.com/problems/number-complement/" target="_blank">https://leetcode.com/problems/number-complement/</a></p>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def bitwiseComplement(self, n: int) -> int:
        if n == 0:
            return 1
        ans = 0
        find = False
        for i in range(30, -1, -1):
            b = n & (1 << i)
            if not find and b == 0:
                continue
            find = True
            if b == 0:
                ans |= 1 << i
        return ans
```

```java
class Solution {
    public int bitwiseComplement(int n) {
        if (n == 0) {
            return 1;
        }
        int ans = 0;
        boolean find = false;
        for (int i = 30; i >= 0; --i) {
            int b = n & (1 << i);
            if (!find && b == 0) {
                continue;
            }
            find = true;
            if (b == 0) {
                ans |= (1 << i);
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int bitwiseComplement(int n) {
        if (n == 0) return 1;
        int ans = 0;
        bool find = false;
        for (int i = 30; i >= 0; --i) {
            int b = n & (1 << i);
            if (!find && b == 0) continue;
            find = true;
            if (b == 0) ans |= (1 << i);
        }
        return ans;
    }
};
```

```go
func bitwiseComplement(n int) int {
	if n == 0 {
		return 1
	}
	ans := 0
	find := false
	for i := 30; i >= 0; i-- {
		b := n & (1 << i)
		if !find && b == 0 {
			continue
		}
		find = true
		if b == 0 {
			ans |= (1 << i)
		}
	}
	return ans
}
```

<!-- tabs:end -->

<!-- end -->
