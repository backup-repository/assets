---
title: 1614 Maximum Nesting Depth Of The Parentheses
summary: 1614 Maximum Nesting Depth Of The Parentheses LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1614 Maximum Nesting Depth Of The Parentheses LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1614 Maximum Nesting Depth Of The Parentheses - Solution Explained/problem-solving.webp
    alt: 1614 Maximum Nesting Depth Of The Parentheses
    hiddenInList: true
    hiddenInSingle: false
---


# [1614. Maximum Nesting Depth of the Parentheses](https://leetcode.com/problems/maximum-nesting-depth-of-the-parentheses)


## Description

<p>A string is a <strong>valid parentheses string</strong> (denoted <strong>VPS</strong>) if it meets one of the following:</p>

<ul>
	<li>It is an empty string <code>&quot;&quot;</code>, or a single character not equal to <code>&quot;(&quot;</code> or <code>&quot;)&quot;</code>,</li>
	<li>It can be written as <code>AB</code> (<code>A</code> concatenated with <code>B</code>), where <code>A</code> and <code>B</code> are <strong>VPS</strong>&#39;s, or</li>
	<li>It can be written as <code>(A)</code>, where <code>A</code> is a <strong>VPS</strong>.</li>
</ul>

<p>We can similarly define the <strong>nesting depth</strong> <code>depth(S)</code> of any VPS <code>S</code> as follows:</p>

<ul>
	<li><code>depth(&quot;&quot;) = 0</code></li>
	<li><code>depth(C) = 0</code>, where <code>C</code> is a string with a single character not equal to <code>&quot;(&quot;</code> or <code>&quot;)&quot;</code>.</li>
	<li><code>depth(A + B) = max(depth(A), depth(B))</code>, where <code>A</code> and <code>B</code> are <strong>VPS</strong>&#39;s.</li>
	<li><code>depth(&quot;(&quot; + A + &quot;)&quot;) = 1 + depth(A)</code>, where <code>A</code> is a <strong>VPS</strong>.</li>
</ul>

<p>For example, <code>&quot;&quot;</code>, <code>&quot;()()&quot;</code>, and <code>&quot;()(()())&quot;</code> are <strong>VPS</strong>&#39;s (with nesting depths 0, 1, and 2), and <code>&quot;)(&quot;</code> and <code>&quot;(()&quot;</code> are not <strong>VPS</strong>&#39;s.</p>

<p>Given a <strong>VPS</strong> represented as string <code>s</code>, return <em>the <strong>nesting depth</strong> of </em><code>s</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;(1+(2*3)+((<u>8</u>)/4))+1&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong> Digit 8 is inside of 3 nested parentheses in the string.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;(1)+((2))+(((<u>3</u>)))&quot;
<strong>Output:</strong> 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 100</code></li>
	<li><code>s</code> consists of digits <code>0-9</code> and characters <code>&#39;+&#39;</code>, <code>&#39;-&#39;</code>, <code>&#39;*&#39;</code>, <code>&#39;/&#39;</code>, <code>&#39;(&#39;</code>, and <code>&#39;)&#39;</code>.</li>
	<li>It is guaranteed that parentheses expression <code>s</code> is a <strong>VPS</strong>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def maxDepth(self, s: str) -> int:
        ans = d = 0
        for c in s:
            if c == '(':
                d += 1
                ans = max(ans, d)
            elif c == ')':
                d -= 1
        return ans
```

```java
class Solution {
    public int maxDepth(String s) {
        int ans = 0, d = 0;
        for (int i = 0; i < s.length(); ++i) {
            char c = s.charAt(i);
            if (c == '(') {
                ans = Math.max(ans, ++d);
            } else if (c == ')') {
                --d;
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int maxDepth(string s) {
        int ans = 0, d = 0;
        for (char& c : s) {
            if (c == '(') {
                ans = max(ans, ++d);
            } else if (c == ')') {
                --d;
            }
        }
        return ans;
    }
};
```

```go
func maxDepth(s string) (ans int) {
	d := 0
	for _, c := range s {
		if c == '(' {
			d++
			ans = max(ans, d)
		} else if c == ')' {
			d--
		}
	}
	return
}
```

```ts
function maxDepth(s: string): number {
    let ans = 0;
    let d = 0;
    for (const c of s) {
        if (c === '(') {
            ans = Math.max(ans, ++d);
        } else if (c === ')') {
            --d;
        }
    }
    return ans;
}
```

```js
/**
 * @param {string} s
 * @return {number}
 */
var maxDepth = function (s) {
    let ans = 0;
    let d = 0;
    for (const c of s) {
        if (c === '(') {
            ans = Math.max(ans, ++d);
        } else if (c === ')') {
            --d;
        }
    }
    return ans;
};
```

```cs
public class Solution {
    public int MaxDepth(string s) {
        int ans = 0, d = 0;
        foreach(char c in s) {
            if (c == '(') {
                ans = Math.Max(ans, ++d);
            } else if (c == ')') {
                --d;
            }
        }
        return ans;
    }
}
```

<!-- tabs:end -->

<!-- end -->
