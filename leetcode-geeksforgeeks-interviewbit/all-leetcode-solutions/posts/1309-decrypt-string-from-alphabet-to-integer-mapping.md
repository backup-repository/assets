---
title: 1309 Decrypt String From Alphabet To Integer Mapping
summary: 1309 Decrypt String From Alphabet To Integer Mapping LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1309 Decrypt String From Alphabet To Integer Mapping LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1309 Decrypt String From Alphabet To Integer Mapping - Solution Explained/problem-solving.webp
    alt: 1309 Decrypt String From Alphabet To Integer Mapping
    hiddenInList: true
    hiddenInSingle: false
---


# [1309. Decrypt String from Alphabet to Integer Mapping](https://leetcode.com/problems/decrypt-string-from-alphabet-to-integer-mapping)


## Description

<p>You are given a string <code>s</code> formed by digits and <code>&#39;#&#39;</code>. We want to map <code>s</code> to English lowercase characters as follows:</p>

<ul>
	<li>Characters (<code>&#39;a&#39;</code> to <code>&#39;i&#39;</code>) are represented by (<code>&#39;1&#39;</code> to <code>&#39;9&#39;</code>) respectively.</li>
	<li>Characters (<code>&#39;j&#39;</code> to <code>&#39;z&#39;</code>) are represented by (<code>&#39;10#&#39;</code> to <code>&#39;26#&#39;</code>) respectively.</li>
</ul>

<p>Return <em>the string formed after mapping</em>.</p>

<p>The test cases are generated so that a unique mapping will always exist.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;10#11#12&quot;
<strong>Output:</strong> &quot;jkab&quot;
<strong>Explanation:</strong> &quot;j&quot; -&gt; &quot;10#&quot; , &quot;k&quot; -&gt; &quot;11#&quot; , &quot;a&quot; -&gt; &quot;1&quot; , &quot;b&quot; -&gt; &quot;2&quot;.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;1326#&quot;
<strong>Output:</strong> &quot;acz&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 1000</code></li>
	<li><code>s</code> consists of digits and the <code>&#39;#&#39;</code> letter.</li>
	<li><code>s</code> will be a valid string such that mapping is always possible.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def freqAlphabets(self, s: str) -> str:
        def get(s):
            return chr(ord('a') + int(s) - 1)

        i, n = 0, len(s)
        res = []
        while i < n:
            if i + 2 < n and s[i + 2] == '#':
                res.append(get(s[i : i + 2]))
                i += 3
            else:
                res.append(get(s[i]))
                i += 1
        return ''.join(res)
```

```java
class Solution {
    public String freqAlphabets(String s) {
        int i = 0, n = s.length();
        StringBuilder res = new StringBuilder();
        while (i < n) {
            if (i + 2 < n && s.charAt(i + 2) == '#') {
                res.append(get(s.substring(i, i + 2)));
                i += 3;
            } else {
                res.append(get(s.substring(i, i + 1)));
                i += 1;
            }
        }
        return res.toString();
    }

    private char get(String s) {
        return (char) ('a' + Integer.parseInt(s) - 1);
    }
}
```

```ts
function freqAlphabets(s: string): string {
    const n = s.length;
    const ans = [];
    let i = 0;
    while (i < n) {
        if (s[i + 2] == '#') {
            ans.push(s.slice(i, i + 2));
            i += 3;
        } else {
            ans.push(s[i]);
            i += 1;
        }
    }
    return ans.map(c => String.fromCharCode('a'.charCodeAt(0) + Number(c) - 1)).join('');
}
```

```rust
impl Solution {
    pub fn freq_alphabets(s: String) -> String {
        let s = s.as_bytes();
        let n = s.len();
        let mut res = String::new();
        let mut i = 0;
        while i < n {
            let code: u8;
            if s.get(i + 2).is_some() && s[i + 2] == b'#' {
                code = (s[i] - b'0') * 10 + s[i + 1];
                i += 3;
            } else {
                code = s[i];
                i += 1;
            }
            res.push(char::from(('a' as u8) + code - b'1'));
        }
        res
    }
}
```

```c
char* freqAlphabets(char* s) {
    int n = strlen(s);
    int i = 0;
    int j = 0;
    char* ans = malloc(sizeof(s) * n);
    while (i < n) {
        int t;
        if (i + 2 < n && s[i + 2] == '#') {
            t = (s[i] - '0') * 10 + s[i + 1];
            i += 3;
        } else {
            t = s[i];
            i += 1;
        }
        ans[j++] = 'a' + t - '1';
    }
    ans[j] = '\0';
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
