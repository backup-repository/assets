---
title: 2771 Longest Non Decreasing Subarray From Two Arrays
summary: 2771 Longest Non Decreasing Subarray From Two Arrays LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "2771 Longest Non Decreasing Subarray From Two Arrays LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2771 Longest Non Decreasing Subarray From Two Arrays - Solution Explained/problem-solving.webp
    alt: 2771 Longest Non Decreasing Subarray From Two Arrays
    hiddenInList: true
    hiddenInSingle: false
---


# [2771. Longest Non-decreasing Subarray From Two Arrays](https://leetcode.com/problems/longest-non-decreasing-subarray-from-two-arrays)


## Description

<p>You are given two <strong>0-indexed</strong> integer arrays <code>nums1</code> and <code>nums2</code> of length <code>n</code>.</p>

<p>Let&#39;s define another <strong>0-indexed</strong> integer array, <code>nums3</code>, of length <code>n</code>. For each index <code>i</code> in the range <code>[0, n - 1]</code>, you can assign either <code>nums1[i]</code> or <code>nums2[i]</code> to <code>nums3[i]</code>.</p>

<p>Your task is to maximize the length of the <strong>longest non-decreasing subarray</strong> in <code>nums3</code> by choosing its values optimally.</p>

<p>Return <em>an integer representing the length of the <strong>longest non-decreasing</strong> subarray in</em> <code>nums3</code>.</p>

<p><strong>Note: </strong>A <strong>subarray</strong> is a contiguous <strong>non-empty</strong> sequence of elements within an array.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [2,3,1], nums2 = [1,2,1]
<strong>Output:</strong> 2
<strong>Explanation: </strong>One way to construct nums3 is: 
nums3 = [nums1[0], nums2[1], nums2[2]] =&gt; [2,2,1]. 
The subarray starting from index 0 and ending at index 1, [2,2], forms a non-decreasing subarray of length 2. 
We can show that 2 is the maximum achievable length.</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [1,3,2,1], nums2 = [2,2,3,4]
<strong>Output:</strong> 4
<strong>Explanation:</strong> One way to construct nums3 is: 
nums3 = [nums1[0], nums2[1], nums2[2], nums2[3]] =&gt; [1,2,3,4]. 
The entire array forms a non-decreasing subarray of length 4, making it the maximum achievable length.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [1,1], nums2 = [2,2]
<strong>Output:</strong> 2
<strong>Explanation:</strong> One way to construct nums3 is: 
nums3 = [nums1[0], nums1[1]] =&gt; [1,1]. 
The entire array forms a non-decreasing subarray of length 2, making it the maximum achievable length.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums1.length == nums2.length == n &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums1[i], nums2[i] &lt;= 10<sup>9</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def maxNonDecreasingLength(self, nums1: List[int], nums2: List[int]) -> int:
        n = len(nums1)
        f = g = 1
        ans = 1
        for i in range(1, n):
            ff = gg = 1
            if nums1[i] >= nums1[i - 1]:
                ff = max(ff, f + 1)
            if nums1[i] >= nums2[i - 1]:
                ff = max(ff, g + 1)
            if nums2[i] >= nums1[i - 1]:
                gg = max(gg, f + 1)
            if nums2[i] >= nums2[i - 1]:
                gg = max(gg, g + 1)
            f, g = ff, gg
            ans = max(ans, f, g)
        return ans
```

```java
class Solution {
    public int maxNonDecreasingLength(int[] nums1, int[] nums2) {
        int n = nums1.length;
        int f = 1, g = 1;
        int ans = 1;
        for (int i = 1; i < n; ++i) {
            int ff = 1, gg = 1;
            if (nums1[i] >= nums1[i - 1]) {
                ff = Math.max(ff, f + 1);
            }
            if (nums1[i] >= nums2[i - 1]) {
                ff = Math.max(ff, g + 1);
            }
            if (nums2[i] >= nums1[i - 1]) {
                gg = Math.max(gg, f + 1);
            }
            if (nums2[i] >= nums2[i - 1]) {
                gg = Math.max(gg, g + 1);
            }
            f = ff;
            g = gg;
            ans = Math.max(ans, Math.max(f, g));
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int maxNonDecreasingLength(vector<int>& nums1, vector<int>& nums2) {
        int n = nums1.size();
        int f = 1, g = 1;
        int ans = 1;
        for (int i = 1; i < n; ++i) {
            int ff = 1, gg = 1;
            if (nums1[i] >= nums1[i - 1]) {
                ff = max(ff, f + 1);
            }
            if (nums1[i] >= nums2[i - 1]) {
                ff = max(ff, g + 1);
            }
            if (nums2[i] >= nums1[i - 1]) {
                gg = max(gg, f + 1);
            }
            if (nums2[i] >= nums2[i - 1]) {
                gg = max(gg, g + 1);
            }
            f = ff;
            g = gg;
            ans = max(ans, max(f, g));
        }
        return ans;
    }
};
```

```go
func maxNonDecreasingLength(nums1 []int, nums2 []int) int {
	n := len(nums1)
	f, g, ans := 1, 1, 1
	for i := 1; i < n; i++ {
		ff, gg := 1, 1
		if nums1[i] >= nums1[i-1] {
			ff = max(ff, f+1)
		}
		if nums1[i] >= nums2[i-1] {
			ff = max(ff, g+1)
		}
		if nums2[i] >= nums1[i-1] {
			gg = max(gg, f+1)
		}
		if nums2[i] >= nums2[i-1] {
			gg = max(gg, g+1)
		}
		f, g = ff, gg
		ans = max(ans, max(f, g))
	}
	return ans
}
```

```ts
function maxNonDecreasingLength(nums1: number[], nums2: number[]): number {
    const n = nums1.length;
    let [f, g, ans] = [1, 1, 1];
    for (let i = 1; i < n; ++i) {
        let [ff, gg] = [1, 1];
        if (nums1[i] >= nums1[i - 1]) {
            ff = Math.max(ff, f + 1);
        }
        if (nums1[i] >= nums2[i - 1]) {
            ff = Math.max(ff, g + 1);
        }
        if (nums2[i] >= nums1[i - 1]) {
            gg = Math.max(gg, f + 1);
        }
        if (nums2[i] >= nums2[i - 1]) {
            gg = Math.max(gg, g + 1);
        }
        f = ff;
        g = gg;
        ans = Math.max(ans, f, g);
    }
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
