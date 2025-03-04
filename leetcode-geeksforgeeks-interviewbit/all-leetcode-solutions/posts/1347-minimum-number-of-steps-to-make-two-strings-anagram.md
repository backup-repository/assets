---
title: 1347 Minimum Number Of Steps To Make Two Strings Anagram
summary: 1347 Minimum Number Of Steps To Make Two Strings Anagram LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1347 Minimum Number Of Steps To Make Two Strings Anagram LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1347 Minimum Number Of Steps To Make Two Strings Anagram - Solution Explained/problem-solving.webp
    alt: 1347 Minimum Number Of Steps To Make Two Strings Anagram
    hiddenInList: true
    hiddenInSingle: false
---


# [1347. Minimum Number of Steps to Make Two Strings Anagram](https://leetcode.com/problems/minimum-number-of-steps-to-make-two-strings-anagram)


## Description

<p>You are given two strings of the same length <code>s</code> and <code>t</code>. In one step you can choose <strong>any character</strong> of <code>t</code> and replace it with <strong>another character</strong>.</p>

<p>Return <em>the minimum number of steps</em> to make <code>t</code> an anagram of <code>s</code>.</p>

<p>An <strong>Anagram</strong> of a string is a string that contains the same characters with a different (or the same) ordering.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;bab&quot;, t = &quot;aba&quot;
<strong>Output:</strong> 1
<strong>Explanation:</strong> Replace the first &#39;a&#39; in t with b, t = &quot;bba&quot; which is anagram of s.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;leetcode&quot;, t = &quot;practice&quot;
<strong>Output:</strong> 5
<strong>Explanation:</strong> Replace &#39;p&#39;, &#39;r&#39;, &#39;a&#39;, &#39;i&#39; and &#39;c&#39; from t with proper characters to make t anagram of s.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;anagram&quot;, t = &quot;mangaar&quot;
<strong>Output:</strong> 0
<strong>Explanation:</strong> &quot;anagram&quot; and &quot;mangaar&quot; are anagrams. 
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>s.length == t.length</code></li>
	<li><code>s</code> and <code>t</code> consist of lowercase English letters only.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def minSteps(self, s: str, t: str) -> int:
        cnt = Counter(s)
        ans = 0
        for c in t:
            if cnt[c] > 0:
                cnt[c] -= 1
            else:
                ans += 1
        return ans
```

```java
class Solution {
    public int minSteps(String s, String t) {
        int[] cnt = new int[26];
        for (int i = 0; i < s.length(); ++i) {
            ++cnt[s.charAt(i) - 'a'];
        }
        int ans = 0;
        for (int i = 0; i < t.length(); ++i) {
            if (--cnt[t.charAt(i) - 'a'] < 0) {
                ++ans;
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int minSteps(string s, string t) {
        int cnt[26]{};
        for (char& c : s) ++cnt[c - 'a'];
        int ans = 0;
        for (char& c : t) {
            ans += --cnt[c - 'a'] < 0;
        }
        return ans;
    }
};
```

```go
func minSteps(s string, t string) (ans int) {
	cnt := [26]int{}
	for _, c := range s {
		cnt[c-'a']++
	}
	for _, c := range t {
		cnt[c-'a']--
		if cnt[c-'a'] < 0 {
			ans++
		}
	}
	return
}
```

```js
/**
 * @param {string} s
 * @param {string} t
 * @return {number}
 */
var minSteps = function (s, t) {
    const cnt = new Array(26).fill(0);
    for (const c of s) {
        const i = c.charCodeAt(0) - 'a'.charCodeAt(0);
        ++cnt[i];
    }
    let ans = 0;
    for (const c of t) {
        const i = c.charCodeAt(0) - 'a'.charCodeAt(0);
        ans += --cnt[i] < 0;
    }
    return ans;
};
```

<!-- tabs:end -->

<!-- end -->
