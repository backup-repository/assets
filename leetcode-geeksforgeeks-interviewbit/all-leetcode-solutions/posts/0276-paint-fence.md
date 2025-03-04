---
title: 0276 Paint Fence
summary: 0276 Paint Fence LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "0276 Paint Fence LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0276 Paint Fence - Solution Explained/problem-solving.webp
    alt: 0276 Paint Fence
    hiddenInList: true
    hiddenInSingle: false
---


# [276. Paint Fence](https://leetcode.com/problems/paint-fence)


## Description

<p>You are painting a fence of <code>n</code> posts with <code>k</code> different colors. You must paint the posts following these rules:</p>

<ul>
	<li>Every post must be painted <strong>exactly one</strong> color.</li>
	<li>There <strong>cannot</strong> be three or more <strong>consecutive</strong> posts with the same color.</li>
</ul>

<p>Given the two integers <code>n</code> and <code>k</code>, return <em>the <strong>number of ways</strong> you can paint the fence</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/solution/0200-0299/0276.Paint%20Fence/images/paintfenceex1.png" style="width: 507px; height: 313px;" />
<pre>
<strong>Input:</strong> n = 3, k = 2
<strong>Output:</strong> 6
<strong>Explanation: </strong>All the possibilities are shown.
Note that painting all the posts red or all the posts green is invalid because there cannot be three posts in a row with the same color.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 1, k = 1
<strong>Output:</strong> 1
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 7, k = 2
<strong>Output:</strong> 42
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 50</code></li>
	<li><code>1 &lt;= k &lt;= 10<sup>5</sup></code></li>
	<li>The testcases are generated such that the answer is in the range <code>[0, 2<sup>31</sup> - 1]</code> for the given <code>n</code> and <code>k</code>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def numWays(self, n: int, k: int) -> int:
        dp = [[0] * 2 for _ in range(n)]
        dp[0][0] = k
        for i in range(1, n):
            dp[i][0] = (dp[i - 1][0] + dp[i - 1][1]) * (k - 1)
            dp[i][1] = dp[i - 1][0]
        return sum(dp[-1])
```

```java
class Solution {
    public int numWays(int n, int k) {
        int[][] dp = new int[n][2];
        dp[0][0] = k;
        for (int i = 1; i < n; ++i) {
            dp[i][0] = (dp[i - 1][0] + dp[i - 1][1]) * (k - 1);
            dp[i][1] = dp[i - 1][0];
        }
        return dp[n - 1][0] + dp[n - 1][1];
    }
}
```

```cpp
class Solution {
public:
    int numWays(int n, int k) {
        vector<vector<int>> dp(n, vector<int>(2));
        dp[0][0] = k;
        for (int i = 1; i < n; ++i) {
            dp[i][0] = (dp[i - 1][0] + dp[i - 1][1]) * (k - 1);
            dp[i][1] = dp[i - 1][0];
        }
        return dp[n - 1][0] + dp[n - 1][1];
    }
};
```

```go
func numWays(n int, k int) int {
	dp := make([][]int, n)
	for i := range dp {
		dp[i] = make([]int, 2)
	}
	dp[0][0] = k
	for i := 1; i < n; i++ {
		dp[i][0] = (dp[i-1][0] + dp[i-1][1]) * (k - 1)
		dp[i][1] = dp[i-1][0]
	}
	return dp[n-1][0] + dp[n-1][1]
}
```

<!-- tabs:end -->

<!-- end -->
