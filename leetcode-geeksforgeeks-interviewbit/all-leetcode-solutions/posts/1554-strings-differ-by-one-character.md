---
title: 1554 Strings Differ By One Character
summary: 1554 Strings Differ By One Character LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1554 Strings Differ By One Character LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1554 Strings Differ By One Character - Solution Explained/problem-solving.webp
    alt: 1554 Strings Differ By One Character
    hiddenInList: true
    hiddenInSingle: false
---


# [1554. Strings Differ by One Character](https://leetcode.com/problems/strings-differ-by-one-character)


## Description

<p>Given a list of strings <code>dict</code> where all the strings are of the same length.</p>

<p>Return <code>true</code> if there are 2 strings that only differ by 1 character in the same index, otherwise return <code>false</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> dict = [&quot;abcd&quot;,&quot;acbd&quot;, &quot;aacd&quot;]
<strong>Output:</strong> true
<strong>Explanation:</strong> Strings &quot;a<strong>b</strong>cd&quot; and &quot;a<strong>a</strong>cd&quot; differ only by one character in the index 1.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> dict = [&quot;ab&quot;,&quot;cd&quot;,&quot;yz&quot;]
<strong>Output:</strong> false
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> dict = [&quot;abcd&quot;,&quot;cccc&quot;,&quot;abyd&quot;,&quot;abab&quot;]
<strong>Output:</strong> true
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of characters in <code>dict &lt;= 10<sup>5</sup></code></li>
	<li><code>dict[i].length == dict[j].length</code></li>
	<li><code>dict[i]</code> should be unique.</li>
	<li><code>dict[i]</code> contains only lowercase English letters.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> Could you solve this problem in <code>O(n * m)</code> where n is the length of <code>dict</code> and <code>m</code> is the length of each string.</p>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def differByOne(self, dict: List[str]) -> bool:
        s = set()
        for word in dict:
            for i in range(len(word)):
                t = word[:i] + "*" + word[i + 1 :]
                if t in s:
                    return True
                s.add(t)
        return False
```

```java
class Solution {
    public boolean differByOne(String[] dict) {
        Set<String> s = new HashSet<>();
        for (String word : dict) {
            for (int i = 0; i < word.length(); ++i) {
                String t = word.substring(0, i) + "*" + word.substring(i + 1);
                if (s.contains(t)) {
                    return true;
                }
                s.add(t);
            }
        }
        return false;
    }
}
```

```cpp
class Solution {
public:
    bool differByOne(vector<string>& dict) {
        unordered_set<string> s;
        for (auto word : dict) {
            for (int i = 0; i < word.size(); ++i) {
                auto t = word;
                t[i] = '*';
                if (s.count(t)) return true;
                s.insert(t);
            }
        }
        return false;
    }
};
```

```go
func differByOne(dict []string) bool {
	s := make(map[string]bool)
	for _, word := range dict {
		for i := range word {
			t := word[:i] + "*" + word[i+1:]
			if s[t] {
				return true
			}
			s[t] = true
		}
	}
	return false
}
```

<!-- tabs:end -->

<!-- end -->
