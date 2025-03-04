---
title: 2108 Find First Palindromic String In The Array
summary: 2108 Find First Palindromic String In The Array LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "2108 Find First Palindromic String In The Array LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2108 Find First Palindromic String In The Array - Solution Explained/problem-solving.webp
    alt: 2108 Find First Palindromic String In The Array
    hiddenInList: true
    hiddenInSingle: false
---


# [2108. Find First Palindromic String in the Array](https://leetcode.com/problems/find-first-palindromic-string-in-the-array)


## Description

<p>Given an array of strings <code>words</code>, return <em>the first <strong>palindromic</strong> string in the array</em>. If there is no such string, return <em>an <strong>empty string</strong> </em><code>&quot;&quot;</code>.</p>

<p>A string is <strong>palindromic</strong> if it reads the same forward and backward.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;abc&quot;,&quot;car&quot;,&quot;ada&quot;,&quot;racecar&quot;,&quot;cool&quot;]
<strong>Output:</strong> &quot;ada&quot;
<strong>Explanation:</strong> The first string that is palindromic is &quot;ada&quot;.
Note that &quot;racecar&quot; is also palindromic, but it is not the first.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;notapalindrome&quot;,&quot;racecar&quot;]
<strong>Output:</strong> &quot;racecar&quot;
<strong>Explanation:</strong> The first and only string that is palindromic is &quot;racecar&quot;.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;def&quot;,&quot;ghi&quot;]
<strong>Output:</strong> &quot;&quot;
<strong>Explanation:</strong> There are no palindromic strings, so the empty string is returned.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= words.length &lt;= 100</code></li>
	<li><code>1 &lt;= words[i].length &lt;= 100</code></li>
	<li><code>words[i]</code> consists only of lowercase English letters.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def firstPalindrome(self, words: List[str]) -> str:
        return next((w for w in words if w == w[::-1]), "")
```

```java
class Solution {
    public String firstPalindrome(String[] words) {
        for (var w : words) {
            boolean ok = true;
            for (int i = 0, j = w.length() - 1; i < j && ok; ++i, --j) {
                if (w.charAt(i) != w.charAt(j)) {
                    ok = false;
                }
            }
            if (ok) {
                return w;
            }
        }
        return "";
    }
}
```

```cpp
class Solution {
public:
    string firstPalindrome(vector<string>& words) {
        for (auto& w : words) {
            bool ok = true;
            for (int i = 0, j = w.size() - 1; i < j; ++i, --j) {
                if (w[i] != w[j]) {
                    ok = false;
                }
            }
            if (ok) {
                return w;
            }
        }
        return "";
    }
};
```

```go
func firstPalindrome(words []string) string {
	for _, w := range words {
		ok := true
		for i, j := 0, len(w)-1; i < j && ok; i, j = i+1, j-1 {
			if w[i] != w[j] {
				ok = false
			}
		}
		if ok {
			return w
		}
	}
	return ""
}
```

```ts
function firstPalindrome(words: string[]): string {
    for (const word of words) {
        let left = 0;
        let right = word.length - 1;
        while (left < right) {
            if (word[left] !== word[right]) {
                break;
            }
            left++;
            right--;
        }
        if (left >= right) {
            return word;
        }
    }
    return '';
}
```

```rust
impl Solution {
    pub fn first_palindrome(words: Vec<String>) -> String {
        for word in words.iter() {
            let s = word.as_bytes();
            let mut left = 0;
            let mut right = s.len() - 1;
            while left < right {
                if s[left] != s[right] {
                    break;
                }
                left += 1;
                right -= 1;
            }
            if left >= right {
                return word.clone();
            }
        }
        String::new()
    }
}
```

```c
char* firstPalindrome(char** words, int wordsSize) {
    for (int i = 0; i < wordsSize; i++) {
        int left = 0;
        int right = strlen(words[i]) - 1;
        while (left < right) {
            if (words[i][left] != words[i][right]) {
                break;
            }
            left++;
            right--;
        }
        if (left >= right) {
            return words[i];
        }
    }
    return "";
}
```

<!-- tabs:end -->

<!-- end -->
