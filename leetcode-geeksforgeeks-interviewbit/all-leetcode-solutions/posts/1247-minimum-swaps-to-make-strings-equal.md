---
title: 1247 Minimum Swaps To Make Strings Equal
summary: 1247 Minimum Swaps To Make Strings Equal LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1247 Minimum Swaps To Make Strings Equal LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1247 Minimum Swaps To Make Strings Equal - Solution Explained/problem-solving.webp
    alt: 1247 Minimum Swaps To Make Strings Equal
    hiddenInList: true
    hiddenInSingle: false
---


# [1247. Minimum Swaps to Make Strings Equal](https://leetcode.com/problems/minimum-swaps-to-make-strings-equal)


## Description

<p>You are given two strings <code>s1</code> and <code>s2</code> of equal length consisting of letters <code>&quot;x&quot;</code> and <code>&quot;y&quot;</code> <strong>only</strong>. Your task is to make these two strings equal to each other. You can swap any two characters that belong to <strong>different</strong> strings, which means: swap <code>s1[i]</code> and <code>s2[j]</code>.</p>

<p>Return the minimum number of swaps required to make <code>s1</code> and <code>s2</code> equal, or return <code>-1</code> if it is impossible to do so.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s1 = &quot;xx&quot;, s2 = &quot;yy&quot;
<strong>Output:</strong> 1
<strong>Explanation:</strong> Swap s1[0] and s2[1], s1 = &quot;yx&quot;, s2 = &quot;yx&quot;.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s1 = &quot;xy&quot;, s2 = &quot;yx&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> Swap s1[0] and s2[0], s1 = &quot;yy&quot;, s2 = &quot;xx&quot;.
Swap s1[0] and s2[1], s1 = &quot;xy&quot;, s2 = &quot;xy&quot;.
Note that you cannot swap s1[0] and s1[1] to make s1 equal to &quot;yx&quot;, cause we can only swap chars in different strings.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s1 = &quot;xx&quot;, s2 = &quot;xy&quot;
<strong>Output:</strong> -1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s1.length, s2.length &lt;= 1000</code></li>
	<li><code>s1.length == s2.length</code></li>
	<li><code>s1, s2</code> only contain <code>&#39;x&#39;</code> or <code>&#39;y&#39;</code>.</li>
</ul>

## Solutions

### Solution 1: Greedy

According to the problem description, both strings $s1$ and $s2$ only contain characters $x$ and $y$, and have the same length. Therefore, we can pair the characters in $s1$ and $s2$, i.e., $s1[i]$ and $s2[i]$.

If $s1[i] = s2[i]$, no swap is needed, and we can skip it. If $s1[i] \neq s2[i]$, a swap is needed. We count the combination of $s1[i]$ and $s2[i]$, i.e., the situation where $s1[i] = x$ and $s2[i] = y$, denoted as $xy$, and the situation where $s1[i] = y$ and $s2[i] = x$, denoted as $yx$.

If $xy + yx$ is odd, the swap cannot be completed, and we return $-1$. If $xy + yx$ is even, the number of swaps needed is $\left \lfloor \frac{x}{2} \right \rfloor$ + $\left \lfloor \frac{y}{2} \right \rfloor$ + $xy \bmod{2}$ + $yx \bmod{2}$.

The time complexity is $O(n)$, where $n$ is the length of the strings $s1$ and $s2$. The space complexity is $O(1)$.

<!-- tabs:start -->

```python
class Solution:
    def minimumSwap(self, s1: str, s2: str) -> int:
        xy = yx = 0
        for a, b in zip(s1, s2):
            xy += a < b
            yx += a > b
        if (xy + yx) % 2:
            return -1
        return xy // 2 + yx // 2 + xy % 2 + yx % 2
```

```java
class Solution {
    public int minimumSwap(String s1, String s2) {
        int xy = 0, yx = 0;
        for (int i = 0; i < s1.length(); ++i) {
            char a = s1.charAt(i), b = s2.charAt(i);
            if (a < b) {
                ++xy;
            }
            if (a > b) {
                ++yx;
            }
        }
        if ((xy + yx) % 2 == 1) {
            return -1;
        }
        return xy / 2 + yx / 2 + xy % 2 + yx % 2;
    }
}
```

```cpp
class Solution {
public:
    int minimumSwap(string s1, string s2) {
        int xy = 0, yx = 0;
        for (int i = 0; i < s1.size(); ++i) {
            char a = s1[i], b = s2[i];
            xy += a < b;
            yx += a > b;
        }
        if ((xy + yx) % 2) {
            return -1;
        }
        return xy / 2 + yx / 2 + xy % 2 + yx % 2;
    }
};
```

```go
func minimumSwap(s1 string, s2 string) int {
	xy, yx := 0, 0
	for i := range s1 {
		if s1[i] < s2[i] {
			xy++
		}
		if s1[i] > s2[i] {
			yx++
		}
	}
	if (xy+yx)%2 == 1 {
		return -1
	}
	return xy/2 + yx/2 + xy%2 + yx%2
}
```

```js
var minimumSwap = function (s1, s2) {
    let xy = 0,
        yx = 0;
    for (let i = 0; i < s1.length; ++i) {
        const a = s1[i],
            b = s2[i];
        if (a < b) {
            ++xy;
        }
        if (a > b) {
            ++yx;
        }
    }
    if ((xy + yx) % 2 === 1) {
        return -1;
    }
    return Math.floor(xy / 2) + Math.floor(yx / 2) + (xy % 2) + (yx % 2);
};
```

<!-- tabs:end -->

<!-- end -->
