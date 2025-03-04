---
title: 1668 Maximum Repeating Substring
summary: 1668 Maximum Repeating Substring LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1668 Maximum Repeating Substring LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1668 Maximum Repeating Substring - Solution Explained/problem-solving.webp
    alt: 1668 Maximum Repeating Substring
    hiddenInList: true
    hiddenInSingle: false
---


# [1668. Maximum Repeating Substring](https://leetcode.com/problems/maximum-repeating-substring)


## Description

<p>For a string <code>sequence</code>, a string <code>word</code> is <strong><code>k</code>-repeating</strong> if <code>word</code> concatenated <code>k</code> times is a substring of <code>sequence</code>. The <code>word</code>&#39;s <strong>maximum <code>k</code>-repeating value</strong> is the highest value <code>k</code> where <code>word</code> is <code>k</code>-repeating in <code>sequence</code>. If <code>word</code> is not a substring of <code>sequence</code>, <code>word</code>&#39;s maximum <code>k</code>-repeating value is <code>0</code>.</p>

<p>Given strings <code>sequence</code> and <code>word</code>, return <em>the <strong>maximum <code>k</code>-repeating value</strong> of <code>word</code> in <code>sequence</code></em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> sequence = &quot;ababc&quot;, word = &quot;ab&quot;
<strong>Output:</strong> 2
<strong>Explanation: </strong>&quot;abab&quot; is a substring in &quot;<u>abab</u>c&quot;.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> sequence = &quot;ababc&quot;, word = &quot;ba&quot;
<strong>Output:</strong> 1
<strong>Explanation: </strong>&quot;ba&quot; is a substring in &quot;a<u>ba</u>bc&quot;. &quot;baba&quot; is not a substring in &quot;ababc&quot;.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> sequence = &quot;ababc&quot;, word = &quot;ac&quot;
<strong>Output:</strong> 0
<strong>Explanation: </strong>&quot;ac&quot; is not a substring in &quot;ababc&quot;. 
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= sequence.length &lt;= 100</code></li>
	<li><code>1 &lt;= word.length &lt;= 100</code></li>
	<li><code>sequence</code> and <code>word</code>&nbsp;contains only lowercase English letters.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def maxRepeating(self, sequence: str, word: str) -> int:
        for k in range(len(sequence) // len(word), -1, -1):
            if word * k in sequence:
                return k
```

```java
class Solution {
    public int maxRepeating(String sequence, String word) {
        for (int k = sequence.length() / word.length(); k > 0; --k) {
            if (sequence.contains(word.repeat(k))) {
                return k;
            }
        }
        return 0;
    }
}
```

```cpp
class Solution {
public:
    int maxRepeating(string sequence, string word) {
        int ans = 0;
        string t = word;
        int x = sequence.size() / word.size();
        for (int k = 1; k <= x; ++k) {
            // C++ 这里从小到大枚举重复值
            if (sequence.find(t) != string::npos) {
                ans = k;
            }
            t += word;
        }
        return ans;
    }
};
```

```go
func maxRepeating(sequence string, word string) int {
	for k := len(sequence) / len(word); k > 0; k-- {
		if strings.Contains(sequence, strings.Repeat(word, k)) {
			return k
		}
	}
	return 0
}
```

```ts
function maxRepeating(sequence: string, word: string): number {
    let n = sequence.length;
    let m = word.length;
    for (let k = Math.floor(n / m); k > 0; k--) {
        if (sequence.includes(word.repeat(k))) {
            return k;
        }
    }
    return 0;
}
```

```rust
impl Solution {
    pub fn max_repeating(sequence: String, word: String) -> i32 {
        let n = sequence.len();
        let m = word.len();
        if n < m {
            return 0;
        }
        let mut dp = vec![0; n - m + 1];
        for i in 0..=n - m {
            let s = &sequence[i..i + m];
            if s == word {
                dp[i] = (if (i as i32) - (m as i32) < 0 { 0 } else { dp[i - m] }) + 1;
            }
        }
        *dp.iter().max().unwrap()
    }
}
```

```c
#define max(a, b) (((a) > (b)) ? (a) : (b))

int findWord(int i, char* sequence, char* word) {
    int n = strlen(word);
    for (int j = 0; j < n; j++) {
        if (sequence[j + i] != word[j]) {
            return 0;
        }
    }
    return 1 + findWord(i + n, sequence, word);
}

int maxRepeating(char* sequence, char* word) {
    int n = strlen(sequence);
    int m = strlen(word);
    int ans = 0;
    for (int i = 0; i <= n - m; i++) {
        ans = max(ans, findWord(i, sequence, word));
    }
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
