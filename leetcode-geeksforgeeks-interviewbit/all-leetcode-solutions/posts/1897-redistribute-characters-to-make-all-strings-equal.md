---
title: 1897 Redistribute Characters To Make All Strings Equal
summary: 1897 Redistribute Characters To Make All Strings Equal LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1897 Redistribute Characters To Make All Strings Equal LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1897 Redistribute Characters To Make All Strings Equal - Solution Explained/problem-solving.webp
    alt: 1897 Redistribute Characters To Make All Strings Equal
    hiddenInList: true
    hiddenInSingle: false
---


# [1897. Redistribute Characters to Make All Strings Equal](https://leetcode.com/problems/redistribute-characters-to-make-all-strings-equal)


## Description

<p>You are given an array of strings <code>words</code> (<strong>0-indexed</strong>).</p>

<p>In one operation, pick two <strong>distinct</strong> indices <code>i</code> and <code>j</code>, where <code>words[i]</code> is a non-empty string, and move <strong>any</strong> character from <code>words[i]</code> to <strong>any</strong> position in <code>words[j]</code>.</p>

<p>Return <code>true</code> <em>if you can make<strong> every</strong> string in </em><code>words</code><em> <strong>equal </strong>using <strong>any</strong> number of operations</em>,<em> and </em><code>false</code> <em>otherwise</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;abc&quot;,&quot;aabc&quot;,&quot;bc&quot;]
<strong>Output:</strong> true
<strong>Explanation:</strong> Move the first &#39;a&#39; in <code>words[1] to the front of words[2],
to make </code><code>words[1]</code> = &quot;abc&quot; and words[2] = &quot;abc&quot;.
All the strings are now equal to &quot;abc&quot;, so return <code>true</code>.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;ab&quot;,&quot;a&quot;]
<strong>Output:</strong> false
<strong>Explanation:</strong> It is impossible to make all the strings equal using the operation.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= words.length &lt;= 100</code></li>
	<li><code>1 &lt;= words[i].length &lt;= 100</code></li>
	<li><code>words[i]</code> consists of lowercase English letters.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def makeEqual(self, words: List[str]) -> bool:
        counter = Counter()
        for word in words:
            for c in word:
                counter[c] += 1
        n = len(words)
        return all(count % n == 0 for count in counter.values())
```

```java
class Solution {
    public boolean makeEqual(String[] words) {
        int[] counter = new int[26];
        for (String word : words) {
            for (char c : word.toCharArray()) {
                ++counter[c - 'a'];
            }
        }
        int n = words.length;
        for (int i = 0; i < 26; ++i) {
            if (counter[i] % n != 0) {
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
    bool makeEqual(vector<string>& words) {
        vector<int> counter(26, 0);
        for (string word : words) {
            for (char c : word) {
                ++counter[c - 'a'];
            }
        }
        int n = words.size();
        for (int count : counter) {
            if (count % n != 0) return false;
        }
        return true;
    }
};
```

```go
func makeEqual(words []string) bool {
	counter := [26]int{}
	for _, word := range words {
		for _, c := range word {
			counter[c-'a']++
		}
	}
	n := len(words)
	for _, count := range counter {
		if count%n != 0 {
			return false
		}
	}
	return true
}
```

```ts
function makeEqual(words: string[]): boolean {
    let n = words.length;
    let letters = new Array(26).fill(0);
    for (let word of words) {
        for (let i = 0; i < word.length; ++i) {
            ++letters[word.charCodeAt(i) - 97];
        }
    }

    for (let i = 0; i < letters.length; ++i) {
        if (letters[i] % n != 0) {
            return false;
        }
    }
    return true;
}
```

<!-- tabs:end -->

<!-- end -->
