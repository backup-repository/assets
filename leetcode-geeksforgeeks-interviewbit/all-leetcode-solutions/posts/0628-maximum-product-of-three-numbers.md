---
title: 0628 Maximum Product Of Three Numbers
summary: 0628 Maximum Product Of Three Numbers LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "0628 Maximum Product Of Three Numbers LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0628 Maximum Product Of Three Numbers - Solution Explained/problem-solving.webp
    alt: 0628 Maximum Product Of Three Numbers
    hiddenInList: true
    hiddenInSingle: false
---


# [628. Maximum Product of Three Numbers](https://leetcode.com/problems/maximum-product-of-three-numbers)


## Description

<p>Given an integer array <code>nums</code>, <em>find three numbers whose product is maximum and return the maximum product</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [1,2,3]
<strong>Output:</strong> 6
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [1,2,3,4]
<strong>Output:</strong> 24
</pre><p><strong class="example">Example 3:</strong></p>
<pre><strong>Input:</strong> nums = [-1,-2,-3]
<strong>Output:</strong> -6
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= nums.length &lt;=&nbsp;10<sup>4</sup></code></li>
	<li><code>-1000 &lt;= nums[i] &lt;= 1000</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def maximumProduct(self, nums: List[int]) -> int:
        nums.sort()
        a = nums[-1] * nums[-2] * nums[-3]
        b = nums[-1] * nums[0] * nums[1]
        return max(a, b)
```

```java
class Solution {
    public int maximumProduct(int[] nums) {
        Arrays.sort(nums);
        int n = nums.length;
        int a = nums[n - 1] * nums[n - 2] * nums[n - 3];
        int b = nums[n - 1] * nums[0] * nums[1];
        return Math.max(a, b);
    }
}
```

```cpp
class Solution {
public:
    int maximumProduct(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        int n = nums.size();
        int a = nums[n - 1] * nums[n - 2] * nums[n - 3];
        int b = nums[n - 1] * nums[0] * nums[1];
        return max(a, b);
    }
};
```

```go
func maximumProduct(nums []int) int {
	sort.Ints(nums)
	n := len(nums)
	a := nums[n-1] * nums[n-2] * nums[n-3]
	b := nums[n-1] * nums[0] * nums[1]
	if a > b {
		return a
	}
	return b
}
```

```ts
function maximumProduct(nums: number[]): number {
    nums.sort((a, b) => a - b);
    const n = nums.length;
    const a = nums[n - 1] * nums[n - 2] * nums[n - 3];
    const b = nums[n - 1] * nums[0] * nums[1];
    return Math.max(a, b);
}
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```python
class Solution:
    def maximumProduct(self, nums: List[int]) -> int:
        top3 = nlargest(3, nums)
        bottom2 = nlargest(2, nums, key=lambda x: -x)
        return max(top3[0] * top3[1] * top3[2], top3[0] * bottom2[0] * bottom2[1])
```

```java
class Solution {
    public int maximumProduct(int[] nums) {
        final int inf = 1 << 30;
        int mi1 = inf, mi2 = inf;
        int mx1 = -inf, mx2 = -inf, mx3 = -inf;
        for (int x : nums) {
            if (x < mi1) {
                mi2 = mi1;
                mi1 = x;
            } else if (x < mi2) {
                mi2 = x;
            }
            if (x > mx1) {
                mx3 = mx2;
                mx2 = mx1;
                mx1 = x;
            } else if (x > mx2) {
                mx3 = mx2;
                mx2 = x;
            } else if (x > mx3) {
                mx3 = x;
            }
        }
        return Math.max(mi1 * mi2 * mx1, mx1 * mx2 * mx3);
    }
}
```

```cpp
class Solution {
public:
    int maximumProduct(vector<int>& nums) {
        const int inf = 1 << 30;
        int mi1 = inf, mi2 = inf;
        int mx1 = -inf, mx2 = -inf, mx3 = -inf;
        for (int x : nums) {
            if (x < mi1) {
                mi2 = mi1;
                mi1 = x;
            } else if (x < mi2) {
                mi2 = x;
            }
            if (x > mx1) {
                mx3 = mx2;
                mx2 = mx1;
                mx1 = x;
            } else if (x > mx2) {
                mx3 = mx2;
                mx2 = x;
            } else if (x > mx3) {
                mx3 = x;
            }
        }
        return max(mi1 * mi2 * mx1, mx1 * mx2 * mx3);
    }
};
```

```go
func maximumProduct(nums []int) int {
	const inf = 1 << 30
	mi1, mi2 := inf, inf
	mx1, mx2, mx3 := -inf, -inf, -inf
	for _, x := range nums {
		if x < mi1 {
			mi1, mi2 = x, mi1
		} else if x < mi2 {
			mi2 = x
		}
		if x > mx1 {
			mx1, mx2, mx3 = x, mx1, mx2
		} else if x > mx2 {
			mx2, mx3 = x, mx2
		} else if x > mx3 {
			mx3 = x
		}
	}
	return max(mi1*mi2*mx1, mx1*mx2*mx3)
}
```

```ts
function maximumProduct(nums: number[]): number {
    const inf = 1 << 30;
    let mi1 = inf,
        mi2 = inf;
    let mx1 = -inf,
        mx2 = -inf,
        mx3 = -inf;
    for (const x of nums) {
        if (x < mi1) {
            mi2 = mi1;
            mi1 = x;
        } else if (x < mi2) {
            mi2 = x;
        }
        if (x > mx1) {
            mx3 = mx2;
            mx2 = mx1;
            mx1 = x;
        } else if (x > mx2) {
            mx3 = mx2;
            mx2 = x;
        } else if (x > mx3) {
            mx3 = x;
        }
    }
    return Math.max(mi1 * mi2 * mx1, mx1 * mx2 * mx3);
}
```

<!-- tabs:end -->

<!-- end -->
