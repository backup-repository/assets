---
title: 1239 Maximum Length Of A Concatenated String With Unique Characters
summary: 1239 Maximum Length Of A Concatenated String With Unique Characters LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1239 Maximum Length Of A Concatenated String With Unique Characters LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1239 Maximum Length Of A Concatenated String With Unique Characters - Solution Explained/problem-solving.webp
    alt: 1239 Maximum Length Of A Concatenated String With Unique Characters
    hiddenInList: true
    hiddenInSingle: false
---


# [1239. Maximum Length of a Concatenated String with Unique Characters](https://leetcode.com/problems/maximum-length-of-a-concatenated-string-with-unique-characters)


## Description

<p>You are given an array of strings <code>arr</code>. A string <code>s</code> is formed by the <strong>concatenation</strong> of a <strong>subsequence</strong> of <code>arr</code> that has <strong>unique characters</strong>.</p>

<p>Return <em>the <strong>maximum</strong> possible length</em> of <code>s</code>.</p>

<p>A <strong>subsequence</strong> is an array that can be derived from another array by deleting some or no elements without changing the order of the remaining elements.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr = [&quot;un&quot;,&quot;iq&quot;,&quot;ue&quot;]
<strong>Output:</strong> 4
<strong>Explanation:</strong> All the valid concatenations are:
- &quot;&quot;
- &quot;un&quot;
- &quot;iq&quot;
- &quot;ue&quot;
- &quot;uniq&quot; (&quot;un&quot; + &quot;iq&quot;)
- &quot;ique&quot; (&quot;iq&quot; + &quot;ue&quot;)
Maximum length is 4.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr = [&quot;cha&quot;,&quot;r&quot;,&quot;act&quot;,&quot;ers&quot;]
<strong>Output:</strong> 6
<strong>Explanation:</strong> Possible longest valid concatenations are &quot;chaers&quot; (&quot;cha&quot; + &quot;ers&quot;) and &quot;acters&quot; (&quot;act&quot; + &quot;ers&quot;).
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> arr = [&quot;abcdefghijklmnopqrstuvwxyz&quot;]
<strong>Output:</strong> 26
<strong>Explanation:</strong> The only string in arr has all 26 characters.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 16</code></li>
	<li><code>1 &lt;= arr[i].length &lt;= 26</code></li>
	<li><code>arr[i]</code> contains only lowercase English letters.</li>
</ul>

## Solutions

### Solution 1: Bit Manipulation + State Compression

State compression is used, with a 32-bit number recording the occurrence of letters, and `masks` storing the strings enumerated before.

The time complexity is $O(2^n + L)$, and the space complexity is $O(2^n)$. Where $n$ and $L$ are the length of the string array and the sum of the lengths of the strings in the array, respectively.

<!-- tabs:start -->

```python
class Solution:
    def maxLength(self, arr: List[str]) -> int:
        ans = 0
        masks = [0]
        for s in arr:
            mask = 0
            for c in s:
                i = ord(c) - ord('a')
                if mask >> i & 1:
                    mask = 0
                    break
                mask |= 1 << i
            if mask == 0:
                continue
            for m in masks:
                if m & mask == 0:
                    masks.append(m | mask)
                    ans = max(ans, (m | mask).bit_count())
        return ans
```

```java
class Solution {
    public int maxLength(List<String> arr) {
        int ans = 0;
        List<Integer> masks = new ArrayList<>();
        masks.add(0);
        for (var s : arr) {
            int mask = 0;
            for (int i = 0; i < s.length(); ++i) {
                int j = s.charAt(i) - 'a';
                if (((mask >> j) & 1) == 1) {
                    mask = 0;
                    break;
                }
                mask |= 1 << j;
            }
            if (mask == 0) {
                continue;
            }
            int n = masks.size();
            for (int i = 0; i < n; ++i) {
                int m = masks.get(i);
                if ((m & mask) == 0) {
                    masks.add(m | mask);
                    ans = Math.max(ans, Integer.bitCount(m | mask));
                }
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int maxLength(vector<string>& arr) {
        int ans = 0;
        vector<int> masks = {0};
        for (auto& s : arr) {
            int mask = 0;
            for (auto& c : s) {
                int i = c - 'a';
                if (mask >> i & 1) {
                    mask = 0;
                    break;
                }
                mask |= 1 << i;
            }
            if (mask == 0) {
                continue;
            }
            int n = masks.size();
            for (int i = 0; i < n; ++i) {
                int m = masks[i];
                if ((m & mask) == 0) {
                    masks.push_back(m | mask);
                    ans = max(ans, __builtin_popcount(m | mask));
                }
            }
        }
        return ans;
    }
};
```

```go
func maxLength(arr []string) (ans int) {
	masks := []int{0}
	for _, s := range arr {
		mask := 0
		for _, c := range s {
			i := int(c - 'a')
			if mask>>i&1 == 1 {
				mask = 0
				break
			}
			mask |= 1 << i
		}
		if mask == 0 {
			continue
		}
		n := len(masks)
		for _, m := range masks[:n] {
			if m&mask == 0 {
				masks = append(masks, m|mask)
				ans = max(ans, bits.OnesCount(uint(m|mask)))
			}
		}
	}
	return
}
```

<!-- tabs:end -->

<!-- end -->
