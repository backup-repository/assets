---
title: 2396 Strictly Palindromic Number
summary: 2396 Strictly Palindromic Number LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "2396 Strictly Palindromic Number LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2396 Strictly Palindromic Number - Solution Explained/problem-solving.webp
    alt: 2396 Strictly Palindromic Number
    hiddenInList: true
    hiddenInSingle: false
---


# [2396. Strictly Palindromic Number](https://leetcode.com/problems/strictly-palindromic-number)


## Description

<p>An integer <code>n</code> is <strong>strictly palindromic</strong> if, for <strong>every</strong> base <code>b</code> between <code>2</code> and <code>n - 2</code> (<strong>inclusive</strong>), the string representation of the integer <code>n</code> in base <code>b</code> is <strong>palindromic</strong>.</p>

<p>Given an integer <code>n</code>, return <code>true</code> <em>if </em><code>n</code><em> is <strong>strictly palindromic</strong> and </em><code>false</code><em> otherwise</em>.</p>

<p>A string is <strong>palindromic</strong> if it reads the same forward and backward.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 9
<strong>Output:</strong> false
<strong>Explanation:</strong> In base 2: 9 = 1001 (base 2), which is palindromic.
In base 3: 9 = 100 (base 3), which is not palindromic.
Therefore, 9 is not strictly palindromic so we return false.
Note that in bases 4, 5, 6, and 7, n = 9 is also not palindromic.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 4
<strong>Output:</strong> false
<strong>Explanation:</strong> We only consider base 2: 4 = 100 (base 2), which is not palindromic.
Therefore, we return false.

</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>4 &lt;= n &lt;= 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def isStrictlyPalindromic(self, n: int) -> bool:
        return False
```

```java
class Solution {
    public boolean isStrictlyPalindromic(int n) {
        return false;
    }
}
```

```cpp
class Solution {
public:
    bool isStrictlyPalindromic(int n) {
        return false;
    }
};
```

```go
func isStrictlyPalindromic(n int) bool {
	return false
}
```

```ts
function isStrictlyPalindromic(n: number): boolean {
    return false;
}
```

```rust
impl Solution {
    pub fn is_strictly_palindromic(n: i32) -> bool {
        false
    }
}
```

```c
bool isStrictlyPalindromic(int n) {
    return 0;
}
```

<!-- tabs:end -->

<!-- end -->
