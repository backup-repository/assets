---
title: 0908 Smallest Range I
summary: 0908 Smallest Range I LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "0908 Smallest Range I LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0908 Smallest Range I - Solution Explained/problem-solving.webp
    alt: 0908 Smallest Range I
    hiddenInList: true
    hiddenInSingle: false
---


# [908. Smallest Range I](https://leetcode.com/problems/smallest-range-i)


## Description

<p>You are given an integer array <code>nums</code> and an integer <code>k</code>.</p>

<p>In one operation, you can choose any index <code>i</code> where <code>0 &lt;= i &lt; nums.length</code> and change <code>nums[i]</code> to <code>nums[i] + x</code> where <code>x</code> is an integer from the range <code>[-k, k]</code>. You can apply this operation <strong>at most once</strong> for each index <code>i</code>.</p>

<p>The <strong>score</strong> of <code>nums</code> is the difference between the maximum and minimum elements in <code>nums</code>.</p>

<p>Return <em>the minimum <strong>score</strong> of </em><code>nums</code><em> after applying the mentioned operation at most once for each index in it</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1], k = 0
<strong>Output:</strong> 0
<strong>Explanation:</strong> The score is max(nums) - min(nums) = 1 - 1 = 0.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [0,10], k = 2
<strong>Output:</strong> 6
<strong>Explanation:</strong> Change nums to be [2, 8]. The score is max(nums) - min(nums) = 8 - 2 = 6.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,3,6], k = 3
<strong>Output:</strong> 0
<strong>Explanation:</strong> Change nums to be [4, 4, 4]. The score is max(nums) - min(nums) = 4 - 4 = 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= k &lt;= 10<sup>4</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def smallestRangeI(self, nums: List[int], k: int) -> int:
        mx, mi = max(nums), min(nums)
        return max(0, mx - mi - k * 2)
```

```java
class Solution {
    public int smallestRangeI(int[] nums, int k) {
        int mx = 0;
        int mi = 10000;
        for (int v : nums) {
            mx = Math.max(mx, v);
            mi = Math.min(mi, v);
        }
        return Math.max(0, mx - mi - k * 2);
    }
}
```

```cpp
class Solution {
public:
    int smallestRangeI(vector<int>& nums, int k) {
        auto [mi, mx] = minmax_element(nums.begin(), nums.end());
        return max(0, *mx - *mi - k * 2);
    }
};
```

```go
func smallestRangeI(nums []int, k int) int {
	mi, mx := slices.Min(nums), slices.Max(nums)
	return max(0, mx-mi-k*2)
}
```

```ts
function smallestRangeI(nums: number[], k: number): number {
    const max = nums.reduce((r, v) => Math.max(r, v));
    const min = nums.reduce((r, v) => Math.min(r, v));
    return Math.max(max - min - k * 2, 0);
}
```

```rust
impl Solution {
    pub fn smallest_range_i(nums: Vec<i32>, k: i32) -> i32 {
        let max = nums.iter().max().unwrap();
        let min = nums.iter().min().unwrap();
        (0).max(max - min - k * 2)
    }
}
```

<!-- tabs:end -->

<!-- end -->
