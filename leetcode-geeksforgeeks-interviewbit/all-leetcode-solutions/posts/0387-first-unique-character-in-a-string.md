---
title: 0387 First Unique Character In A String
summary: 0387 First Unique Character In A String LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "0387 First Unique Character In A String LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0387 First Unique Character In A String - Solution Explained/problem-solving.webp
    alt: 0387 First Unique Character In A String
    hiddenInList: true
    hiddenInSingle: false
---


# [387. First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string)


## Description

<p>Given a string <code>s</code>, <em>find the first non-repeating character in it and return its index</em>. If it does not exist, return <code>-1</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> s = "leetcode"
<strong>Output:</strong> 0
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> s = "loveleetcode"
<strong>Output:</strong> 2
</pre><p><strong class="example">Example 3:</strong></p>
<pre><strong>Input:</strong> s = "aabb"
<strong>Output:</strong> -1
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> consists of only lowercase English letters.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def firstUniqChar(self, s: str) -> int:
        cnt = Counter(s)
        for i, c in enumerate(s):
            if cnt[c] == 1:
                return i
        return -1
```

```java
class Solution {
    public int firstUniqChar(String s) {
        int[] cnt = new int[26];
        int n = s.length();
        for (int i = 0; i < n; ++i) {
            ++cnt[s.charAt(i) - 'a'];
        }
        for (int i = 0; i < n; ++i) {
            if (cnt[s.charAt(i) - 'a'] == 1) {
                return i;
            }
        }
        return -1;
    }
}
```

```cpp
class Solution {
public:
    int firstUniqChar(string s) {
        int cnt[26]{};
        for (char& c : s) {
            ++cnt[c - 'a'];
        }
        int n = s.size();
        for (int i = 0; i < n; ++i) {
            if (cnt[s[i] - 'a'] == 1) {
                return i;
            }
        }
        return -1;
    }
};
```

```go
func firstUniqChar(s string) int {
	cnt := [26]int{}
	for _, c := range s {
		cnt[c-'a']++
	}
	for i, c := range s {
		if cnt[c-'a'] == 1 {
			return i
		}
	}
	return -1
}
```

```ts
function firstUniqChar(s: string): number {
    const cnt = new Array(26).fill(0);
    for (const c of s) {
        cnt[c.charCodeAt(0) - 97]++;
    }
    for (let i = 0; i < s.length; i++) {
        if (cnt[s.charCodeAt(i) - 97] === 1) {
            return i;
        }
    }
    return -1;
}
```

```js
/**
 * @param {string} s
 * @return {number}
 */
var firstUniqChar = function (s) {
    const cnt = new Array(26).fill(0);
    for (const c of s) {
        ++cnt[c.charCodeAt() - 'a'.charCodeAt()];
    }
    for (let i = 0; i < s.length; ++i) {
        if (cnt[s[i].charCodeAt() - 'a'.charCodeAt()] === 1) {
            return i;
        }
    }
    return -1;
};
```

```php
class Solution {
    /**
     * @param String $s
     * @return Integer
     */
    function firstUniqChar($s) {
        for ($i = 0; $i < strlen($s); $i++) {
            $hashtable[$s[$i]]++;
        }
        for ($i = 0; $i < strlen($s); $i++) {
            if ($hashtable[$s[$i]] == 1) {
                return $i;
            }
        }
        return -1;
    }
}
```

<!-- tabs:end -->

<!-- end -->
