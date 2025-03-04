---
title: 0330 Patching Array
summary: 0330 Patching Array LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "0330 Patching Array LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0330 Patching Array - Solution Explained/problem-solving.webp
    alt: 0330 Patching Array
    hiddenInList: true
    hiddenInSingle: false
---


# [330. Patching Array](https://leetcode.com/problems/patching-array)


## Description

<p>Given a sorted integer array <code>nums</code> and an integer <code>n</code>, add/patch elements to the array such that any number in the range <code>[1, n]</code> inclusive can be formed by the sum of some elements in the array.</p>

<p>Return <em>the minimum number of patches required</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,3], n = 6
<strong>Output:</strong> 1
Explanation:
Combinations of nums are [1], [3], [1,3], which form possible sums of: 1, 3, 4.
Now if we add/patch 2 to nums, the combinations are: [1], [2], [3], [1,3], [2,3], [1,2,3].
Possible sums are 1, 2, 3, 4, 5, 6, which now covers the range [1, 6].
So we only need 1 patch.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,5,10], n = 20
<strong>Output:</strong> 2
Explanation: The two patches can be [2, 4].
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,2], n = 5
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 1000</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
	<li><code>nums</code> is sorted in <strong>ascending order</strong>.</li>
	<li><code>1 &lt;= n &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def minPatches(self, nums: List[int], n: int) -> int:
        x = 1
        ans = i = 0
        while x <= n:
            if i < len(nums) and nums[i] <= x:
                x += nums[i]
                i += 1
            else:
                ans += 1
                x <<= 1
        return ans
```

```java
class Solution {
    public int minPatches(int[] nums, int n) {
        long x = 1;
        int ans = 0;
        for (int i = 0; x <= n;) {
            if (i < nums.length && nums[i] <= x) {
                x += nums[i++];
            } else {
                ++ans;
                x <<= 1;
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int minPatches(vector<int>& nums, int n) {
        long long x = 1;
        int ans = 0;
        for (int i = 0; x <= n;) {
            if (i < nums.size() && nums[i] <= x) {
                x += nums[i++];
            } else {
                ++ans;
                x <<= 1;
            }
        }
        return ans;
    }
};
```

```go
func minPatches(nums []int, n int) (ans int) {
	x := 1
	for i := 0; x <= n; {
		if i < len(nums) && nums[i] <= x {
			x += nums[i]
			i++
		} else {
			ans++
			x <<= 1
		}
	}
	return
}
```

```ts
function minPatches(nums: number[], n: number): number {
    let x = 1;
    let ans = 0;
    for (let i = 0; x <= n; ) {
        if (i < nums.length && nums[i] <= x) {
            x += nums[i++];
        } else {
            ++ans;
            x *= 2;
        }
    }
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
