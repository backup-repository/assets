---
title: 0713 Subarray Product Less Than K
summary: 0713 Subarray Product Less Than K LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "0713 Subarray Product Less Than K LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0713 Subarray Product Less Than K - Solution Explained/problem-solving.webp
    alt: 0713 Subarray Product Less Than K
    hiddenInList: true
    hiddenInSingle: false
---


# [713. Subarray Product Less Than K](https://leetcode.com/problems/subarray-product-less-than-k)


## Description

<p>Given an array of integers <code>nums</code> and an integer <code>k</code>, return <em>the number of contiguous subarrays where the product of all the elements in the subarray is strictly less than </em><code>k</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [10,5,2,6], k = 100
<strong>Output:</strong> 8
<strong>Explanation:</strong> The 8 subarrays that have product less than 100 are:
[10], [5], [2], [6], [10, 5], [5, 2], [2, 6], [5, 2, 6]
Note that [10, 5, 2] is not included as the product of 100 is not strictly less than k.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3], k = 0
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 1000</code></li>
	<li><code>0 &lt;= k &lt;= 10<sup>6</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def numSubarrayProductLessThanK(self, nums: List[int], k: int) -> int:
        ans, s, j = 0, 1, 0
        for i, v in enumerate(nums):
            s *= v
            while j <= i and s >= k:
                s //= nums[j]
                j += 1
            ans += i - j + 1
        return ans
```

```java
class Solution {
    public int numSubarrayProductLessThanK(int[] nums, int k) {
        int ans = 0;
        for (int i = 0, j = 0, s = 1; i < nums.length; ++i) {
            s *= nums[i];
            while (j <= i && s >= k) {
                s /= nums[j++];
            }
            ans += i - j + 1;
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int numSubarrayProductLessThanK(vector<int>& nums, int k) {
        int ans = 0;
        for (int i = 0, j = 0, s = 1; i < nums.size(); ++i) {
            s *= nums[i];
            while (j <= i && s >= k) s /= nums[j++];
            ans += i - j + 1;
        }
        return ans;
    }
};
```

```go
func numSubarrayProductLessThanK(nums []int, k int) int {
	ans := 0
	for i, j, s := 0, 0, 1; i < len(nums); i++ {
		s *= nums[i]
		for ; j <= i && s >= k; j++ {
			s /= nums[j]
		}
		ans += i - j + 1
	}
	return ans
}
```

```ts
function numSubarrayProductLessThanK(nums: number[], k: number): number {
    let ans = 0;
    for (let i = 0, j = 0, s = 1; i < nums.length; ++i) {
        s *= nums[i];
        while (j <= i && s >= k) {
            s /= nums[j++];
        }
        ans += i - j + 1;
    }
    return ans;
}
```

```rust
impl Solution {
    pub fn num_subarray_product_less_than_k(nums: Vec<i32>, k: i32) -> i32 {
        if k <= 1 {
            return 0;
        }

        let mut res = 0;
        let mut product = 1;
        let mut i = 0;
        nums.iter()
            .enumerate()
            .for_each(|(j, v)| {
                product *= v;
                while product >= k {
                    product /= nums[i];
                    i += 1;
                }
                res += j - i + 1;
            });
        res as i32
    }
}
```

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var numSubarrayProductLessThanK = function (nums, k) {
    const n = nums.length;
    let ans = 0;
    let s = 1;
    for (let i = 0, j = 0; i < n; ++i) {
        s *= nums[i];
        while (j <= i && s >= k) {
            s = Math.floor(s / nums[j++]);
        }
        ans += i - j + 1;
    }
    return ans;
};
```

<!-- tabs:end -->

<!-- end -->
