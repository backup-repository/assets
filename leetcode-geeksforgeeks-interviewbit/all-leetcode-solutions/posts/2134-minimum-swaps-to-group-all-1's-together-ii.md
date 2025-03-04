---
title: 2134 Minimum Swaps To Group All 1'S Together Ii
summary: 2134 Minimum Swaps To Group All 1'S Together Ii LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "2134 Minimum Swaps To Group All 1'S Together Ii LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2134 Minimum Swaps To Group All 1'S Together Ii - Solution Explained/problem-solving.webp
    alt: 2134 Minimum Swaps To Group All 1'S Together Ii
    hiddenInList: true
    hiddenInSingle: false
---


# [2134. Minimum Swaps to Group All 1's Together II](https://leetcode.com/problems/minimum-swaps-to-group-all-1s-together-ii)


## Description

<p>A <strong>swap</strong> is defined as taking two <strong>distinct</strong> positions in an array and swapping the values in them.</p>

<p>A <strong>circular</strong> array is defined as an array where we consider the <strong>first</strong> element and the <strong>last</strong> element to be <strong>adjacent</strong>.</p>

<p>Given a <strong>binary</strong> <strong>circular</strong> array <code>nums</code>, return <em>the minimum number of swaps required to group all </em><code>1</code><em>&#39;s present in the array together at <strong>any location</strong></em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [0,1,0,1,1,0,0]
<strong>Output:</strong> 1
<strong>Explanation:</strong> Here are a few of the ways to group all the 1&#39;s together:
[0,<u>0</u>,<u>1</u>,1,1,0,0] using 1 swap.
[0,1,<u>1</u>,1,<u>0</u>,0,0] using 1 swap.
[1,1,0,0,0,0,1] using 2 swaps (using the circular property of the array).
There is no way to group all 1&#39;s together with 0 swaps.
Thus, the minimum number of swaps required is 1.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [0,1,1,1,0,0,1,1,0]
<strong>Output:</strong> 2
<strong>Explanation:</strong> Here are a few of the ways to group all the 1&#39;s together:
[1,1,1,0,0,0,0,1,1] using 2 swaps (using the circular property of the array).
[1,1,1,1,1,0,0,0,0] using 2 swaps.
There is no way to group all 1&#39;s together with 0 or 1 swaps.
Thus, the minimum number of swaps required is 2.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,1,0,0,1]
<strong>Output:</strong> 0
<strong>Explanation:</strong> All the 1&#39;s are already grouped together due to the circular property of the array.
Thus, the minimum number of swaps required is 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>nums[i]</code> is either <code>0</code> or <code>1</code>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def minSwaps(self, nums: List[int]) -> int:
        cnt = nums.count(1)
        n = len(nums)
        s = [0] * ((n << 1) + 1)
        for i in range(n << 1):
            s[i + 1] = s[i] + nums[i % n]
        mx = 0
        for i in range(n << 1):
            j = i + cnt - 1
            if j < (n << 1):
                mx = max(mx, s[j + 1] - s[i])
        return cnt - mx
```

```java
class Solution {
    public int minSwaps(int[] nums) {
        int cnt = 0;
        for (int v : nums) {
            cnt += v;
        }
        int n = nums.length;
        int[] s = new int[(n << 1) + 1];
        for (int i = 0; i < (n << 1); ++i) {
            s[i + 1] = s[i] + nums[i % n];
        }
        int mx = 0;
        for (int i = 0; i < (n << 1); ++i) {
            int j = i + cnt - 1;
            if (j < (n << 1)) {
                mx = Math.max(mx, s[j + 1] - s[i]);
            }
        }
        return cnt - mx;
    }
}
```

```cpp
class Solution {
public:
    int minSwaps(vector<int>& nums) {
        int cnt = 0;
        for (int& v : nums) cnt += v;
        int n = nums.size();
        vector<int> s((n << 1) + 1);
        for (int i = 0; i < (n << 1); ++i) s[i + 1] = s[i] + nums[i % n];
        int mx = 0;
        for (int i = 0; i < (n << 1); ++i) {
            int j = i + cnt - 1;
            if (j < (n << 1)) mx = max(mx, s[j + 1] - s[i]);
        }
        return cnt - mx;
    }
};
```

```go
func minSwaps(nums []int) int {
	cnt := 0
	for _, v := range nums {
		cnt += v
	}
	n := len(nums)
	s := make([]int, (n<<1)+1)
	for i := 0; i < (n << 1); i++ {
		s[i+1] = s[i] + nums[i%n]
	}
	mx := 0
	for i := 0; i < (n << 1); i++ {
		j := i + cnt - 1
		if j < (n << 1) {
			mx = max(mx, s[j+1]-s[i])
		}
	}
	return cnt - mx
}
```

```ts
function minSwaps(nums: number[]): number {
    const n = nums.length;
    const m = nums.reduce((a, c) => a + c, 0);
    let cnt = nums.reduce((a, c, i) => a + (i < m ? c : 0), 0);
    let ans = cnt;
    for (let i = m; i < m + n; i++) {
        let prev = nums[i - m];
        let post = nums[i % n];
        cnt += post - prev;
        ans = Math.max(cnt, ans);
    }
    return m - ans;
}
```

<!-- tabs:end -->

<!-- end -->
