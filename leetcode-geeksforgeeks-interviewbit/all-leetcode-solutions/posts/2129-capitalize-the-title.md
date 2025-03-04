---
title: 2129 Capitalize The Title
summary: 2129 Capitalize The Title LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "2129 Capitalize The Title LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2129 Capitalize The Title - Solution Explained/problem-solving.webp
    alt: 2129 Capitalize The Title
    hiddenInList: true
    hiddenInSingle: false
---


# [2129. Capitalize the Title](https://leetcode.com/problems/capitalize-the-title)


## Description

<p>You are given a string <code>title</code> consisting of one or more words separated by a single space, where each word consists of English letters. <strong>Capitalize</strong> the string by changing the capitalization of each word such that:</p>

<ul>
	<li>If the length of the word is <code>1</code> or <code>2</code> letters, change all letters to lowercase.</li>
	<li>Otherwise, change the first letter to uppercase and the remaining letters to lowercase.</li>
</ul>

<p>Return <em>the <strong>capitalized</strong> </em><code>title</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> title = &quot;capiTalIze tHe titLe&quot;
<strong>Output:</strong> &quot;Capitalize The Title&quot;
<strong>Explanation:</strong>
Since all the words have a length of at least 3, the first letter of each word is uppercase, and the remaining letters are lowercase.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> title = &quot;First leTTeR of EACH Word&quot;
<strong>Output:</strong> &quot;First Letter of Each Word&quot;
<strong>Explanation:</strong>
The word &quot;of&quot; has length 2, so it is all lowercase.
The remaining words have a length of at least 3, so the first letter of each remaining word is uppercase, and the remaining letters are lowercase.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> title = &quot;i lOve leetcode&quot;
<strong>Output:</strong> &quot;i Love Leetcode&quot;
<strong>Explanation:</strong>
The word &quot;i&quot; has length 1, so it is lowercase.
The remaining words have a length of at least 3, so the first letter of each remaining word is uppercase, and the remaining letters are lowercase.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= title.length &lt;= 100</code></li>
	<li><code>title</code> consists of words separated by a single space without any leading or trailing spaces.</li>
	<li>Each word consists of uppercase and lowercase English letters and is <strong>non-empty</strong>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def capitalizeTitle(self, title: str) -> str:
        words = [w.lower() if len(w) < 3 else w.capitalize() for w in title.split()]
        return " ".join(words)
```

```java
class Solution {
    public String capitalizeTitle(String title) {
        List<String> ans = new ArrayList<>();
        for (String s : title.split(" ")) {
            if (s.length() < 3) {
                ans.add(s.toLowerCase());
            } else {
                ans.add(s.substring(0, 1).toUpperCase() + s.substring(1).toLowerCase());
            }
        }
        return String.join(" ", ans);
    }
}
```

```cpp
class Solution {
public:
    string capitalizeTitle(string title) {
        transform(title.begin(), title.end(), title.begin(), ::tolower);
        istringstream ss(title);
        string ans;
        while (ss >> title) {
            if (title.size() > 2) title[0] = toupper(title[0]);
            ans += title;
            ans += " ";
        }
        ans.pop_back();
        return ans;
    }
};
```

```go
func capitalizeTitle(title string) string {
	title = strings.ToLower(title)
	words := strings.Split(title, " ")
	for i, s := range words {
		if len(s) > 2 {
			words[i] = strings.Title(s)
		}
	}
	return strings.Join(words, " ")
}
```

```ts
function capitalizeTitle(title: string): string {
    const ans: string[] = [];
    for (const s of title.split(' ')) {
        if (s.length < 3) {
            ans.push(s.toLowerCase());
        } else {
            ans.push(s.substring(0, 1).toUpperCase() + s.substring(1).toLowerCase());
        }
    }
    return ans.join(' ');
}
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```ts
function capitalizeTitle(title: string): string {
    return title
        .split(' ')
        .map(s =>
            s.length < 3
                ? s.toLowerCase()
                : s.substring(0, 1).toUpperCase() + s.substring(1).toLowerCase(),
        )
        .join(' ');
}
```

<!-- tabs:end -->

<!-- end -->
