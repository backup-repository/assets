---
title: 0801 Minimum Swaps To Make Sequences Increasing
summary: 0801 Minimum Swaps To Make Sequences Increasing LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "0801 Minimum Swaps To Make Sequences Increasing LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0801 Minimum Swaps To Make Sequences Increasing - Solution Explained/problem-solving.webp
    alt: 0801 Minimum Swaps To Make Sequences Increasing
    hiddenInList: true
    hiddenInSingle: false
---


# [801. Minimum Swaps To Make Sequences Increasing](https://leetcode.com/problems/minimum-swaps-to-make-sequences-increasing)


## Description

<p>You are given two integer arrays of the same length <code>nums1</code> and <code>nums2</code>. In one operation, you are allowed to swap <code>nums1[i]</code> with <code>nums2[i]</code>.</p>

<ul>
	<li>For example, if <code>nums1 = [1,2,3,<u>8</u>]</code>, and <code>nums2 = [5,6,7,<u>4</u>]</code>, you can swap the element at <code>i = 3</code> to obtain <code>nums1 = [1,2,3,4]</code> and <code>nums2 = [5,6,7,8]</code>.</li>
</ul>

<p>Return <em>the minimum number of needed operations to make </em><code>nums1</code><em> and </em><code>nums2</code><em> <strong>strictly increasing</strong></em>. The test cases are generated so that the given input always makes it possible.</p>

<p>An array <code>arr</code> is <strong>strictly increasing</strong> if and only if <code>arr[0] &lt; arr[1] &lt; arr[2] &lt; ... &lt; arr[arr.length - 1]</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [1,3,5,4], nums2 = [1,2,3,7]
<strong>Output:</strong> 1
<strong>Explanation:</strong> 
Swap nums1[3] and nums2[3]. Then the sequences are:
nums1 = [1, 3, 5, 7] and nums2 = [1, 2, 3, 4]
which are both strictly increasing.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [0,3,5,8,9], nums2 = [2,1,4,6,9]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= nums1.length &lt;= 10<sup>5</sup></code></li>
	<li><code>nums2.length == nums1.length</code></li>
	<li><code>0 &lt;= nums1[i], nums2[i] &lt;= 2 * 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def minSwap(self, nums1: List[int], nums2: List[int]) -> int:
        a, b = 0, 1
        for i in range(1, len(nums1)):
            x, y = a, b
            if nums1[i - 1] >= nums1[i] or nums2[i - 1] >= nums2[i]:
                a, b = y, x + 1
            else:
                b = y + 1
                if nums1[i - 1] < nums2[i] and nums2[i - 1] < nums1[i]:
                    a, b = min(a, y), min(b, x + 1)
        return min(a, b)
```

```java
class Solution {
    public int minSwap(int[] nums1, int[] nums2) {
        int a = 0, b = 1;
        for (int i = 1; i < nums1.length; ++i) {
            int x = a, y = b;
            if (nums1[i - 1] >= nums1[i] || nums2[i - 1] >= nums2[i]) {
                a = y;
                b = x + 1;
            } else {
                b = y + 1;
                if (nums1[i - 1] < nums2[i] && nums2[i - 1] < nums1[i]) {
                    a = Math.min(a, y);
                    b = Math.min(b, x + 1);
                }
            }
        }
        return Math.min(a, b);
    }
}
```

```cpp
class Solution {
public:
    int minSwap(vector<int>& nums1, vector<int>& nums2) {
        int a = 0, b = 1, n = nums1.size();
        for (int i = 1; i < n; ++i) {
            int x = a, y = b;
            if (nums1[i - 1] >= nums1[i] || nums2[i - 1] >= nums2[i]) {
                a = y, b = x + 1;
            } else {
                b = y + 1;
                if (nums1[i - 1] < nums2[i] && nums2[i - 1] < nums1[i]) {
                    a = min(a, y);
                    b = min(b, x + 1);
                }
            }
        }
        return min(a, b);
    }
};
```

```go
func minSwap(nums1 []int, nums2 []int) int {
	a, b, n := 0, 1, len(nums1)
	for i := 1; i < n; i++ {
		x, y := a, b
		if nums1[i-1] >= nums1[i] || nums2[i-1] >= nums2[i] {
			a, b = y, x+1
		} else {
			b = y + 1
			if nums1[i-1] < nums2[i] && nums2[i-1] < nums1[i] {
				a = min(a, y)
				b = min(b, x+1)
			}
		}
	}
	return min(a, b)
}
```

<!-- tabs:end -->

<!-- end -->
