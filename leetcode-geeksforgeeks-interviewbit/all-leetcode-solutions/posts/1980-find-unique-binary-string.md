---
title: 1980 Find Unique Binary String
summary: 1980 Find Unique Binary String LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1980 Find Unique Binary String LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1980 Find Unique Binary String - Solution Explained/problem-solving.webp
    alt: 1980 Find Unique Binary String
    hiddenInList: true
    hiddenInSingle: false
---


# [1980. Find Unique Binary String](https://leetcode.com/problems/find-unique-binary-string)


## Description

<p>Given an array of strings <code>nums</code> containing <code>n</code> <strong>unique</strong> binary strings each of length <code>n</code>, return <em>a binary string of length </em><code>n</code><em> that <strong>does not appear</strong> in </em><code>nums</code><em>. If there are multiple answers, you may return <strong>any</strong> of them</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [&quot;01&quot;,&quot;10&quot;]
<strong>Output:</strong> &quot;11&quot;
<strong>Explanation:</strong> &quot;11&quot; does not appear in nums. &quot;00&quot; would also be correct.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [&quot;00&quot;,&quot;01&quot;]
<strong>Output:</strong> &quot;11&quot;
<strong>Explanation:</strong> &quot;11&quot; does not appear in nums. &quot;10&quot; would also be correct.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [&quot;111&quot;,&quot;011&quot;,&quot;001&quot;]
<strong>Output:</strong> &quot;101&quot;
<strong>Explanation:</strong> &quot;101&quot; does not appear in nums. &quot;000&quot;, &quot;010&quot;, &quot;100&quot;, and &quot;110&quot; would also be correct.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == nums.length</code></li>
	<li><code>1 &lt;= n &lt;= 16</code></li>
	<li><code>nums[i].length == n</code></li>
	<li><code>nums[i] </code>is either <code>&#39;0&#39;</code> or <code>&#39;1&#39;</code>.</li>
	<li>All the strings of <code>nums</code> are <strong>unique</strong>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def findDifferentBinaryString(self, nums: List[str]) -> str:
        mask = 0
        for x in nums:
            mask |= 1 << x.count("1")
        n = len(nums)
        for i in range(n + 1):
            if mask >> i & 1 ^ 1:
                return "1" * i + "0" * (n - i)
```

```java
class Solution {
    public String findDifferentBinaryString(String[] nums) {
        int mask = 0;
        for (var x : nums) {
            int cnt = 0;
            for (int i = 0; i < x.length(); ++i) {
                if (x.charAt(i) == '1') {
                    ++cnt;
                }
            }
            mask |= 1 << cnt;
        }
        for (int i = 0;; ++i) {
            if ((mask >> i & 1) == 0) {
                return "1".repeat(i) + "0".repeat(nums.length - i);
            }
        }
    }
}
```

```cpp
class Solution {
public:
    string findDifferentBinaryString(vector<string>& nums) {
        int mask = 0;
        for (auto& x : nums) {
            int cnt = count(x.begin(), x.end(), '1');
            mask |= 1 << cnt;
        }
        for (int i = 0;; ++i) {
            if (mask >> i & 1 ^ 1) {
                return string(i, '1') + string(nums.size() - i, '0');
            }
        }
    }
};
```

```go
func findDifferentBinaryString(nums []string) string {
	mask := 0
	for _, x := range nums {
		mask |= 1 << strings.Count(x, "1")
	}
	for i := 0; ; i++ {
		if mask>>i&1 == 0 {
			return strings.Repeat("1", i) + strings.Repeat("0", len(nums)-i)
		}
	}
}
```

```cs
public class Solution {
    public string FindDifferentBinaryString(string[] nums) {
        int mask = 0;
        foreach (var x in nums) {
            int cnt = x.Count(c => c == '1');
            mask |= 1 << cnt;
        }
        int i = 0;
        while ((mask >> i & 1) == 1) {
            i++;
        }
        return string.Format("{0}{1}", new string('1', i), new string('0', nums.Length - i));
    }
}
```

<!-- tabs:end -->

<!-- end -->
