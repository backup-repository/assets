---
title: 2330 Valid Palindrome Iv
summary: 2330 Valid Palindrome Iv LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "2330 Valid Palindrome Iv LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2330 Valid Palindrome Iv - Solution Explained/problem-solving.webp
    alt: 2330 Valid Palindrome Iv
    hiddenInList: true
    hiddenInSingle: false
---


# [2330. Valid Palindrome IV](https://leetcode.com/problems/valid-palindrome-iv)


## Description

<p>You are given a <strong>0-indexed</strong> string <code>s</code> consisting of only lowercase English letters. In one operation, you can change <strong>any</strong> character of <code>s</code> to any <strong>other</strong> character.</p>

<p>Return <code>true</code><em> if you can make </em><code>s</code><em> a palindrome after performing <strong>exactly</strong> one or two operations, or return </em><code>false</code><em> otherwise.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abcdba&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> One way to make s a palindrome using 1 operation is:
- Change s[2] to &#39;d&#39;. Now, s = &quot;abddba&quot;.
One operation could be performed to make s a palindrome so return true.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aa&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> One way to make s a palindrome using 2 operations is:
- Change s[0] to &#39;b&#39;. Now, s = &quot;ba&quot;.
- Change s[1] to &#39;b&#39;. Now, s = &quot;bb&quot;.
Two operations could be performed to make s a palindrome so return true.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abcdef&quot;
<strong>Output:</strong> false
<strong>Explanation:</strong> It is not possible to make s a palindrome using one or two operations so return false.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> consists only of lowercase English letters.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def makePalindrome(self, s: str) -> bool:
        i, j = 0, len(s) - 1
        cnt = 0
        while i < j:
            cnt += s[i] != s[j]
            i, j = i + 1, j - 1
        return cnt <= 2
```

```java
class Solution {
    public boolean makePalindrome(String s) {
        int cnt = 0;
        int i = 0, j = s.length() - 1;
        for (; i < j; ++i, --j) {
            if (s.charAt(i) != s.charAt(j)) {
                ++cnt;
            }
        }
        return cnt <= 2;
    }
}
```

```cpp
class Solution {
public:
    bool makePalindrome(string s) {
        int cnt = 0;
        int i = 0, j = s.size() - 1;
        for (; i < j; ++i, --j) {
            cnt += s[i] != s[j];
        }
        return cnt <= 2;
    }
};
```

```go
func makePalindrome(s string) bool {
	cnt := 0
	i, j := 0, len(s)-1
	for ; i < j; i, j = i+1, j-1 {
		if s[i] != s[j] {
			cnt++
		}
	}
	return cnt <= 2
}
```

```ts
function makePalindrome(s: string): boolean {
    let cnt = 0;
    let i = 0;
    let j = s.length - 1;
    for (; i < j; ++i, --j) {
        if (s[i] != s[j]) {
            ++cnt;
        }
    }
    return cnt <= 2;
}
```

<!-- tabs:end -->

<!-- end -->
