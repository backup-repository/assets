---
title: 2789 Largest Element In An Array After Merge Operations
summary: 2789 Largest Element In An Array After Merge Operations LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "2789 Largest Element In An Array After Merge Operations LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2789 Largest Element In An Array After Merge Operations - Solution Explained/problem-solving.webp
    alt: 2789 Largest Element In An Array After Merge Operations
    hiddenInList: true
    hiddenInSingle: false
---


# [2789. Largest Element in an Array after Merge Operations](https://leetcode.com/problems/largest-element-in-an-array-after-merge-operations)


## Description

<p>You are given a <strong>0-indexed</strong> array <code>nums</code> consisting of positive integers.</p>

<p>You can do the following operation on the array <strong>any</strong> number of times:</p>

<ul>
	<li>Choose an integer <code>i</code> such that <code>0 &lt;= i &lt; nums.length - 1</code> and <code>nums[i] &lt;= nums[i + 1]</code>. Replace the element <code>nums[i + 1]</code> with <code>nums[i] + nums[i + 1]</code> and delete the element <code>nums[i]</code> from the array.</li>
</ul>

<p>Return <em>the value of the <b>largest</b> element that you can possibly obtain in the final array.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,3,7,9,3]
<strong>Output:</strong> 21
<strong>Explanation:</strong> We can apply the following operations on the array:
- Choose i = 0. The resulting array will be nums = [<u>5</u>,7,9,3].
- Choose i = 1. The resulting array will be nums = [5,<u>16</u>,3].
- Choose i = 0. The resulting array will be nums = [<u>21</u>,3].
The largest element in the final array is 21. It can be shown that we cannot obtain a larger element.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [5,3,3]
<strong>Output:</strong> 11
<strong>Explanation:</strong> We can do the following operations on the array:
- Choose i = 1. The resulting array will be nums = [5,<u>6</u>].
- Choose i = 0. The resulting array will be nums = [<u>11</u>].
There is only one element in the final array, which is 11.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>6</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def maxArrayValue(self, nums: List[int]) -> int:
        for i in range(len(nums) - 2, -1, -1):
            if nums[i] <= nums[i + 1]:
                nums[i] += nums[i + 1]
        return max(nums)
```

```java
class Solution {
    public long maxArrayValue(int[] nums) {
        int n = nums.length;
        long ans = nums[n - 1], t = nums[n - 1];
        for (int i = n - 2; i >= 0; --i) {
            if (nums[i] <= t) {
                t += nums[i];
            } else {
                t = nums[i];
            }
            ans = Math.max(ans, t);
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    long long maxArrayValue(vector<int>& nums) {
        int n = nums.size();
        long long ans = nums[n - 1], t = nums[n - 1];
        for (int i = n - 2; ~i; --i) {
            if (nums[i] <= t) {
                t += nums[i];
            } else {
                t = nums[i];
            }
            ans = max(ans, t);
        }
        return ans;
    }
};
```

```go
func maxArrayValue(nums []int) int64 {
	n := len(nums)
	ans, t := nums[n-1], nums[n-1]
	for i := n - 2; i >= 0; i-- {
		if nums[i] <= t {
			t += nums[i]
		} else {
			t = nums[i]
		}
		ans = max(ans, t)
	}
	return int64(ans)
}
```

```ts
function maxArrayValue(nums: number[]): number {
    for (let i = nums.length - 2; i >= 0; --i) {
        if (nums[i] <= nums[i + 1]) {
            nums[i] += nums[i + 1];
        }
    }
    return Math.max(...nums);
}
```

<!-- tabs:end -->

<!-- end -->
