---
title: 2490 Circular Sentence
summary: 2490 Circular Sentence LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "2490 Circular Sentence LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2490 Circular Sentence - Solution Explained/problem-solving.webp
    alt: 2490 Circular Sentence
    hiddenInList: true
    hiddenInSingle: false
---


# [2490. Circular Sentence](https://leetcode.com/problems/circular-sentence)


## Description

<p>A <strong>sentence</strong> is a list of words that are separated by a<strong> single</strong> space with no leading or trailing spaces.</p>

<ul>
	<li>For example, <code>&quot;Hello World&quot;</code>, <code>&quot;HELLO&quot;</code>, <code>&quot;hello world hello world&quot;</code> are all sentences.</li>
</ul>

<p>Words consist of <strong>only</strong> uppercase and lowercase English letters. Uppercase and lowercase English letters are considered different.</p>

<p>A sentence is <strong>circular </strong>if:</p>

<ul>
	<li>The last character of a word is equal to the first character of the next word.</li>
	<li>The last character of the last word is equal to the first character of the first word.</li>
</ul>

<p>For example, <code>&quot;leetcode exercises sound delightful&quot;</code>, <code>&quot;eetcode&quot;</code>, <code>&quot;leetcode eats soul&quot; </code>are all circular sentences. However, <code>&quot;Leetcode is cool&quot;</code>, <code>&quot;happy Leetcode&quot;</code>, <code>&quot;Leetcode&quot;</code> and <code>&quot;I like Leetcode&quot;</code> are <strong>not</strong> circular sentences.</p>

<p>Given a string <code>sentence</code>, return <code>true</code><em> if it is circular</em>. Otherwise, return <code>false</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> sentence = &quot;leetcode exercises sound delightful&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> The words in sentence are [&quot;leetcode&quot;, &quot;exercises&quot;, &quot;sound&quot;, &quot;delightful&quot;].
- leetcod<u>e</u>&#39;s&nbsp;last character is equal to <u>e</u>xercises&#39;s first character.
- exercise<u>s</u>&#39;s&nbsp;last character is equal to <u>s</u>ound&#39;s first character.
- soun<u>d</u>&#39;s&nbsp;last character is equal to <u>d</u>elightful&#39;s first character.
- delightfu<u>l</u>&#39;s&nbsp;last character is equal to <u>l</u>eetcode&#39;s first character.
The sentence is circular.</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> sentence = &quot;eetcode&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> The words in sentence are [&quot;eetcode&quot;].
- eetcod<u>e</u>&#39;s&nbsp;last character is equal to <u>e</u>etcode&#39;s first character.
The sentence is circular.</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> sentence = &quot;Leetcode is cool&quot;
<strong>Output:</strong> false
<strong>Explanation:</strong> The words in sentence are [&quot;Leetcode&quot;, &quot;is&quot;, &quot;cool&quot;].
- Leetcod<u>e</u>&#39;s&nbsp;last character is <strong>not</strong> equal to <u>i</u>s&#39;s first character.
The sentence is <strong>not</strong> circular.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= sentence.length &lt;= 500</code></li>
	<li><code>sentence</code> consist of only lowercase and uppercase English letters and spaces.</li>
	<li>The words in <code>sentence</code> are separated by a single space.</li>
	<li>There are no leading or trailing spaces.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def isCircularSentence(self, sentence: str) -> bool:
        ss = sentence.split()
        n = len(ss)
        return all(s[-1] == ss[(i + 1) % n][0] for i, s in enumerate(ss))
```

```java
class Solution {
    public boolean isCircularSentence(String sentence) {
        var ss = sentence.split(" ");
        int n = ss.length;
        for (int i = 0; i < n; ++i) {
            if (ss[i].charAt(ss[i].length() - 1) != ss[(i + 1) % n].charAt(0)) {
                return false;
            }
        }
        return true;
    }
}
```

```cpp
class Solution {
public:
    bool isCircularSentence(string sentence) {
        auto ss = split(sentence, ' ');
        int n = ss.size();
        for (int i = 0; i < n; ++i) {
            if (ss[i].back() != ss[(i + 1) % n][0]) {
                return false;
            }
        }
        return true;
    }

    vector<string> split(string& s, char delim) {
        stringstream ss(s);
        string item;
        vector<string> res;
        while (getline(ss, item, delim)) {
            res.emplace_back(item);
        }
        return res;
    }
};
```

```go
func isCircularSentence(sentence string) bool {
	ss := strings.Split(sentence, " ")
	n := len(ss)
	for i, s := range ss {
		if s[len(s)-1] != ss[(i+1)%n][0] {
			return false
		}
	}
	return true
}
```

```ts
function isCircularSentence(sentence: string): boolean {
    const ss = sentence.split(' ');
    const n = ss.length;
    for (let i = 0; i < n; ++i) {
        if (ss[i][ss[i].length - 1] !== ss[(i + 1) % n][0]) {
            return false;
        }
    }
    return true;
}
```

```rust
impl Solution {
    pub fn is_circular_sentence(sentence: String) -> bool {
        let ss: Vec<String> = sentence.split(' ').map(String::from).collect();
        let n = ss.len();
        for i in 0..n {
            if ss[i].as_bytes()[ss[i].len() - 1] != ss[(i + 1) % n].as_bytes()[0] {
                return false;
            }
        }
        return true;
    }
}
```

```js
/**
 * @param {string} sentence
 * @return {boolean}
 */
var isCircularSentence = function (sentence) {
    const ss = sentence.split(' ');
    const n = ss.length;
    for (let i = 0; i < n; ++i) {
        if (ss[i][ss[i].length - 1] !== ss[(i + 1) % n][0]) {
            return false;
        }
    }
    return true;
};
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```python
class Solution:
    def isCircularSentence(self, s: str) -> bool:
        return s[0] == s[-1] and all(
            c != " " or s[i - 1] == s[i + 1] for i, c in enumerate(s)
        )
```

```java
class Solution {
    public boolean isCircularSentence(String s) {
        int n = s.length();
        if (s.charAt(0) != s.charAt(n - 1)) {
            return false;
        }
        for (int i = 1; i < n; ++i) {
            if (s.charAt(i) == ' ' && s.charAt(i - 1) != s.charAt(i + 1)) {
                return false;
            }
        }
        return true;
    }
}
```

```cpp
class Solution {
public:
    bool isCircularSentence(string s) {
        int n = s.size();
        if (s[0] != s.back()) {
            return false;
        }
        for (int i = 1; i < n; ++i) {
            if (s[i] == ' ' && s[i - 1] != s[i + 1]) {
                return false;
            }
        }
        return true;
    }
};
```

```go
func isCircularSentence(s string) bool {
	n := len(s)
	if s[0] != s[n-1] {
		return false
	}
	for i := 1; i < n; i++ {
		if s[i] == ' ' && s[i-1] != s[i+1] {
			return false
		}
	}
	return true
}
```

```ts
function isCircularSentence(s: string): boolean {
    const n = s.length;
    if (s[0] !== s[n - 1]) {
        return false;
    }
    for (let i = 1; i < n; ++i) {
        if (s[i] === ' ' && s[i - 1] !== s[i + 1]) {
            return false;
        }
    }
    return true;
}
```

```rust
impl Solution {
    pub fn is_circular_sentence(sentence: String) -> bool {
        let n = sentence.len();
        let chars: Vec<char> = sentence.chars().collect();

        if chars[0] != chars[n - 1] {
            return false;
        }

        for i in 1..n - 1 {
            if chars[i] == ' ' && chars[i - 1] != chars[i + 1] {
                return false;
            }
        }

        true
    }
}
```

```js
/**
 * @param {string} s
 * @return {boolean}
 */
var isCircularSentence = function (s) {
    const n = s.length;
    if (s[0] !== s[n - 1]) {
        return false;
    }
    for (let i = 1; i < n; ++i) {
        if (s[i] === ' ' && s[i - 1] !== s[i + 1]) {
            return false;
        }
    }
    return true;
};
```

<!-- tabs:end -->

<!-- end -->
