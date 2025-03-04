---
title: 2297 Jump Game Viii
summary: 2297 Jump Game Viii LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "2297 Jump Game Viii LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2297 Jump Game Viii - Solution Explained/problem-solving.webp
    alt: 2297 Jump Game Viii
    hiddenInList: true
    hiddenInSingle: false
---


# [2297. Jump Game VIII](https://leetcode.com/problems/jump-game-viii)


## Description

<p>You are given a <strong>0-indexed</strong> integer array <code>nums</code> of length <code>n</code>. You are initially standing at index <code>0</code>. You can jump from index <code>i</code> to index <code>j</code> where <code>i &lt; j</code> if:</p>

<ul>
	<li><code>nums[i] &lt;= nums[j]</code> and <code>nums[k] &lt; nums[i]</code> for all indexes <code>k</code> in the range <code>i &lt; k &lt; j</code>, or</li>
	<li><code>nums[i] &gt; nums[j]</code> and <code>nums[k] &gt;= nums[i]</code> for all indexes <code>k</code> in the range <code>i &lt; k &lt; j</code>.</li>
</ul>

<p>You are also given an integer array <code>costs</code> of length <code>n</code> where <code>costs[i]</code> denotes the cost of jumping <strong>to</strong> index <code>i</code>.</p>

<p>Return <em>the <strong>minimum</strong> cost to jump to the index </em><code>n - 1</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,2,4,4,1], costs = [3,7,6,4,2]
<strong>Output:</strong> 8
<strong>Explanation:</strong> You start at index 0.
- Jump to index 2 with a cost of costs[2] = 6.
- Jump to index 4 with a cost of costs[4] = 2.
The total cost is 8. It can be proven that 8 is the minimum cost needed.
Two other possible paths are from index 0 -&gt; 1 -&gt; 4 and index 0 -&gt; 2 -&gt; 3 -&gt; 4.
These have a total cost of 9 and 12, respectively.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [0,1,2], costs = [1,1,1]
<strong>Output:</strong> 2
<strong>Explanation:</strong> Start at index 0.
- Jump to index 1 with a cost of costs[1] = 1.
- Jump to index 2 with a cost of costs[2] = 1.
The total cost is 2. Note that you cannot jump directly from index 0 to index 2 because nums[0] &lt;= nums[1].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == nums.length == costs.length</code></li>
	<li><code>1 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= nums[i], costs[i] &lt;= 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def minCost(self, nums: List[int], costs: List[int]) -> int:
        n = len(nums)
        g = defaultdict(list)
        stk = []
        for i in range(n - 1, -1, -1):
            while stk and nums[stk[-1]] < nums[i]:
                stk.pop()
            if stk:
                g[i].append(stk[-1])
            stk.append(i)

        stk = []
        for i in range(n - 1, -1, -1):
            while stk and nums[stk[-1]] >= nums[i]:
                stk.pop()
            if stk:
                g[i].append(stk[-1])
            stk.append(i)

        f = [inf] * n
        f[0] = 0
        for i in range(n):
            for j in g[i]:
                f[j] = min(f[j], f[i] + costs[j])
        return f[n - 1]
```

```java
class Solution {
    public long minCost(int[] nums, int[] costs) {
        int n = nums.length;
        List<Integer>[] g = new List[n];
        Arrays.setAll(g, k -> new ArrayList<>());
        Deque<Integer> stk = new ArrayDeque<>();
        for (int i = n - 1; i >= 0; --i) {
            while (!stk.isEmpty() && nums[stk.peek()] < nums[i]) {
                stk.pop();
            }
            if (!stk.isEmpty()) {
                g[i].add(stk.peek());
            }
            stk.push(i);
        }
        stk.clear();
        for (int i = n - 1; i >= 0; --i) {
            while (!stk.isEmpty() && nums[stk.peek()] >= nums[i]) {
                stk.pop();
            }
            if (!stk.isEmpty()) {
                g[i].add(stk.peek());
            }
            stk.push(i);
        }
        long[] f = new long[n];
        Arrays.fill(f, 1L << 60);
        f[0] = 0;
        for (int i = 0; i < n; ++i) {
            for (int j : g[i]) {
                f[j] = Math.min(f[j], f[i] + costs[j]);
            }
        }
        return f[n - 1];
    }
}
```

```cpp
class Solution {
public:
    long long minCost(vector<int>& nums, vector<int>& costs) {
        int n = nums.size();
        vector<int> g[n];
        stack<int> stk;
        for (int i = n - 1; ~i; --i) {
            while (!stk.empty() && nums[stk.top()] < nums[i]) {
                stk.pop();
            }
            if (!stk.empty()) {
                g[i].push_back(stk.top());
            }
            stk.push(i);
        }
        stk = stack<int>();
        for (int i = n - 1; ~i; --i) {
            while (!stk.empty() && nums[stk.top()] >= nums[i]) {
                stk.pop();
            }
            if (!stk.empty()) {
                g[i].push_back(stk.top());
            }
            stk.push(i);
        }
        vector<long long> f(n, 1e18);
        f[0] = 0;
        for (int i = 0; i < n; ++i) {
            for (int j : g[i]) {
                f[j] = min(f[j], f[i] + costs[j]);
            }
        }
        return f[n - 1];
    }
};
```

```go
func minCost(nums []int, costs []int) int64 {
	n := len(nums)
	g := make([][]int, n)
	stk := []int{}
	for i := n - 1; i >= 0; i-- {
		for len(stk) > 0 && nums[stk[len(stk)-1]] < nums[i] {
			stk = stk[:len(stk)-1]
		}
		if len(stk) > 0 {
			g[i] = append(g[i], stk[len(stk)-1])
		}
		stk = append(stk, i)
	}
	stk = []int{}
	for i := n - 1; i >= 0; i-- {
		for len(stk) > 0 && nums[stk[len(stk)-1]] >= nums[i] {
			stk = stk[:len(stk)-1]
		}
		if len(stk) > 0 {
			g[i] = append(g[i], stk[len(stk)-1])
		}
		stk = append(stk, i)
	}
	f := make([]int64, n)
	for i := 1; i < n; i++ {
		f[i] = math.MaxInt64
	}
	for i := 0; i < n; i++ {
		for _, j := range g[i] {
			f[j] = min(f[j], f[i]+int64(costs[j]))
		}
	}
	return f[n-1]
}
```

```ts
function minCost(nums: number[], costs: number[]): number {
    const n = nums.length;
    const g: number[][] = Array.from({ length: n }, () => []);
    const stk: number[] = [];
    for (let i = n - 1; i >= 0; --i) {
        while (stk.length && nums[stk[stk.length - 1]] < nums[i]) {
            stk.pop();
        }
        if (stk.length) {
            g[i].push(stk[stk.length - 1]);
        }
        stk.push(i);
    }
    stk.length = 0;
    for (let i = n - 1; i >= 0; --i) {
        while (stk.length && nums[stk[stk.length - 1]] >= nums[i]) {
            stk.pop();
        }
        if (stk.length) {
            g[i].push(stk[stk.length - 1]);
        }
        stk.push(i);
    }
    const f: number[] = Array.from({ length: n }, () => Infinity);
    f[0] = 0;
    for (let i = 0; i < n; ++i) {
        for (const j of g[i]) {
            f[j] = Math.min(f[j], f[i] + costs[j]);
        }
    }
    return f[n - 1];
}
```

<!-- tabs:end -->

<!-- end -->
