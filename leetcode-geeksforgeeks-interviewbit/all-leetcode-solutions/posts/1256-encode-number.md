---
title: 1256 Encode Number
summary: 1256 Encode Number LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1256 Encode Number LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1256 Encode Number - Solution Explained/problem-solving.webp
    alt: 1256 Encode Number
    hiddenInList: true
    hiddenInSingle: false
---


# [1256. Encode Number](https://leetcode.com/problems/encode-number)


## Description

<p>Given a non-negative integer <code>num</code>, Return its <em>encoding</em> string.</p>

<p>The encoding is done by converting the integer to a string using a secret function that you should deduce from the following table:</p>

<p><img alt="" src="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/solution/1200-1299/1256.Encode%20Number/images/encode_number.png" style="width: 164px; height: 360px;" /></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> num = 23
<strong>Output:</strong> &quot;1000&quot;
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> num = 107
<strong>Output:</strong> &quot;101100&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= num &lt;= 10^9</code></li>
</ul>

## Solutions

### Solution 1: Bit Manipulation

We add one to $num$, then convert it to a binary string and remove the highest bit $1$.

The time complexity is $O(\log n)$, and the space complexity is $O(\log n)$. Where $n$ is the size of $num$.

<!-- tabs:start -->

```python
class Solution:
    def encode(self, num: int) -> str:
        return bin(num + 1)[3:]
```

```java
class Solution {
    public String encode(int num) {
        return Integer.toBinaryString(num + 1).substring(1);
    }
}
```

```cpp
class Solution {
public:
    string encode(int num) {
        bitset<32> bs(++num);
        string ans = bs.to_string();
        int i = 0;
        while (ans[i] == '0') {
            ++i;
        }
        return ans.substr(i + 1);
    }
};
```

```go
func encode(num int) string {
	num++
	s := strconv.FormatInt(int64(num), 2)
	return s[1:]
}
```

```ts
function encode(num: number): string {
    ++num;
    let s = num.toString(2);
    return s.slice(1);
}
```

<!-- tabs:end -->

<!-- end -->
