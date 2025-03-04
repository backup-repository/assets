---
title: 0494 Target Sum
summary: 0494 Target Sum LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "0494 Target Sum LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0494 Target Sum - Solution Explained/problem-solving.webp
    alt: 0494 Target Sum
    hiddenInList: true
    hiddenInSingle: false
---


# [494. Target Sum](https://leetcode.com/problems/target-sum)


## Description

<p>You are given an integer array <code>nums</code> and an integer <code>target</code>.</p>

<p>You want to build an <strong>expression</strong> out of nums by adding one of the symbols <code>&#39;+&#39;</code> and <code>&#39;-&#39;</code> before each integer in nums and then concatenate all the integers.</p>

<ul>
	<li>For example, if <code>nums = [2, 1]</code>, you can add a <code>&#39;+&#39;</code> before <code>2</code> and a <code>&#39;-&#39;</code> before <code>1</code> and concatenate them to build the expression <code>&quot;+2-1&quot;</code>.</li>
</ul>

<p>Return the number of different <strong>expressions</strong> that you can build, which evaluates to <code>target</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,1,1,1,1], target = 3
<strong>Output:</strong> 5
<strong>Explanation:</strong> There are 5 ways to assign symbols to make the sum of nums be target 3.
-1 + 1 + 1 + 1 + 1 = 3
+1 - 1 + 1 + 1 + 1 = 3
+1 + 1 - 1 + 1 + 1 = 3
+1 + 1 + 1 - 1 + 1 = 3
+1 + 1 + 1 + 1 - 1 = 3
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1], target = 1
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 20</code></li>
	<li><code>0 &lt;= nums[i] &lt;= 1000</code></li>
	<li><code>0 &lt;= sum(nums[i]) &lt;= 1000</code></li>
	<li><code>-1000 &lt;= target &lt;= 1000</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def findTargetSumWays(self, nums: List[int], target: int) -> int:
        s = sum(nums)
        if s < target or (s - target) % 2 != 0:
            return 0
        m, n = len(nums), (s - target) // 2
        dp = [[0] * (n + 1) for _ in range(m + 1)]
        dp[0][0] = 1
        for i in range(1, m + 1):
            for j in range(n + 1):
                dp[i][j] = dp[i - 1][j]
                if nums[i - 1] <= j:
                    dp[i][j] += dp[i - 1][j - nums[i - 1]]
        return dp[-1][-1]
```

```java
class Solution {
    public int findTargetSumWays(int[] nums, int target) {
        int s = 0;
        for (int v : nums) {
            s += v;
        }
        if (s < target || (s - target) % 2 != 0) {
            return 0;
        }
        int m = nums.length;
        int n = (s - target) / 2;
        int[][] dp = new int[m + 1][n + 1];
        dp[0][0] = 1;
        for (int i = 1; i <= m; ++i) {
            for (int j = 0; j <= n; ++j) {
                dp[i][j] = dp[i - 1][j];
                if (nums[i - 1] <= j) {
                    dp[i][j] += dp[i - 1][j - nums[i - 1]];
                }
            }
        }
        return dp[m][n];
    }
}
```

```cpp
class Solution {
public:
    int findTargetSumWays(vector<int>& nums, int target) {
        int s = accumulate(nums.begin(), nums.end(), 0);
        if (s < target || (s - target) % 2 != 0) return 0;
        int m = nums.size(), n = (s - target) / 2;
        vector<vector<int>> dp(m + 1, vector<int>(n + 1));
        dp[0][0] = 1;
        for (int i = 1; i <= m; ++i) {
            for (int j = 0; j <= n; ++j) {
                dp[i][j] += dp[i - 1][j];
                if (nums[i - 1] <= j) dp[i][j] += dp[i - 1][j - nums[i - 1]];
            }
        }
        return dp[m][n];
    }
};
```

```go
func findTargetSumWays(nums []int, target int) int {
	s := 0
	for _, v := range nums {
		s += v
	}
	if s < target || (s-target)%2 != 0 {
		return 0
	}
	m, n := len(nums), (s-target)/2
	dp := make([][]int, m+1)
	for i := range dp {
		dp[i] = make([]int, n+1)
	}
	dp[0][0] = 1
	for i := 1; i <= m; i++ {
		for j := 0; j <= n; j++ {
			dp[i][j] = dp[i-1][j]
			if nums[i-1] <= j {
				dp[i][j] += dp[i-1][j-nums[i-1]]
			}
		}
	}
	return dp[m][n]
}
```

```rust
impl Solution {
    #[allow(dead_code)]
    pub fn find_target_sum_ways(nums: Vec<i32>, target: i32) -> i32 {
        let mut sum = 0;
        for e in &nums {
            sum += *e;
        }

        // -x + (sum - x) = target <-> -2 * x + sum = target <-> 2 * x = sum - target
        if sum < target || (sum - target) % 2 != 0 {
            // There is no way to get any expression in this case
            return 0;
        }
        let n = nums.len();
        let m = (sum - target) / 2;

        let mut dp: Vec<Vec<i32>> = vec![vec![0; m as usize + 1]; n + 1];

        // Initialize the dp vector
        dp[0][0] = 1;

        // Begin the actual dp phase
        for i in 1..=n {
            for j in 0..=m as usize {
                // nums[i - 1] is not included
                dp[i][j] = dp[i - 1][j];
                if nums[i - 1] <= (j as i32) {
                    // nums[i - 1] is included
                    dp[i][j] += dp[i - 1][j - (nums[i - 1] as usize)];
                }
            }
        }

        dp[n][m as usize]
    }
}
```

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var findTargetSumWays = function (nums, target) {
    let s = 0;
    for (let v of nums) {
        s += v;
    }
    if (s < target || (s - target) % 2 != 0) {
        return 0;
    }
    const m = nums.length;
    const n = (s - target) / 2;
    let dp = new Array(n + 1).fill(0);
    dp[0] = 1;
    for (let i = 1; i <= m; ++i) {
        for (let j = n; j >= nums[i - 1]; --j) {
            dp[j] += dp[j - nums[i - 1]];
        }
    }
    return dp[n];
};
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```python
class Solution:
    def findTargetSumWays(self, nums: List[int], target: int) -> int:
        s = sum(nums)
        if s < target or (s - target) % 2 != 0:
            return 0
        n = (s - target) // 2
        dp = [0] * (n + 1)
        dp[0] = 1
        for v in nums:
            for j in range(n, v - 1, -1):
                dp[j] += dp[j - v]
        return dp[-1]
```

```java
class Solution {
    public int findTargetSumWays(int[] nums, int target) {
        int s = 0;
        for (int v : nums) {
            s += v;
        }
        if (s < target || (s - target) % 2 != 0) {
            return 0;
        }
        int n = (s - target) / 2;
        int[] dp = new int[n + 1];
        dp[0] = 1;
        for (int v : nums) {
            for (int j = n; j >= v; --j) {
                dp[j] += dp[j - v];
            }
        }
        return dp[n];
    }
}
```

```cpp
class Solution {
public:
    int findTargetSumWays(vector<int>& nums, int target) {
        int s = accumulate(nums.begin(), nums.end(), 0);
        if (s < target || (s - target) % 2 != 0) return 0;
        int n = (s - target) / 2;
        vector<int> dp(n + 1);
        dp[0] = 1;
        for (int& v : nums)
            for (int j = n; j >= v; --j)
                dp[j] += dp[j - v];
        return dp[n];
    }
};
```

```go
func findTargetSumWays(nums []int, target int) int {
	s := 0
	for _, v := range nums {
		s += v
	}
	if s < target || (s-target)%2 != 0 {
		return 0
	}
	n := (s - target) / 2
	dp := make([]int, n+1)
	dp[0] = 1
	for _, v := range nums {
		for j := n; j >= v; j-- {
			dp[j] += dp[j-v]
		}
	}
	return dp[n]
}
```

```rust
impl Solution {
    #[allow(dead_code)]
    pub fn find_target_sum_ways(nums: Vec<i32>, target: i32) -> i32 {
        let mut sum = 0;
        for e in &nums {
            sum += *e;
        }

        if sum < target || (sum - target) % 2 != 0 {
            // Just directly return
            return 0;
        }

        let n = ((sum - target) / 2) as usize;
        let mut dp: Vec<i32> = vec![0; n + 1];

        // Initialize the dp vector
        dp[0] = 1;

        // Begin the actual dp phase
        for e in &nums {
            for i in (*e as usize..=n).rev() {
                dp[i] += dp[i - (*e as usize)];
            }
        }

        dp[n]
    }
}
```

<!-- tabs:end -->

### Solution 3

<!-- tabs:start -->

```python
class Solution:
    def findTargetSumWays(self, nums: List[int], target: int) -> int:
        @cache
        def dfs(i, t):
            if i == n:
                if t == target:
                    return 1
                return 0
            return dfs(i + 1, t + nums[i]) + dfs(i + 1, t - nums[i])

        ans, n = 0, len(nums)
        return dfs(0, 0)
```

<!-- tabs:end -->

<!-- end -->
