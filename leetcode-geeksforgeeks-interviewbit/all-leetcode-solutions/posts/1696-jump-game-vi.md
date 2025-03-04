---
title: 1696 Jump Game Vi
summary: 1696 Jump Game Vi LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1696 Jump Game Vi LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1696 Jump Game Vi - Solution Explained/problem-solving.webp
    alt: 1696 Jump Game Vi
    hiddenInList: true
    hiddenInSingle: false
---


# [1696. Jump Game VI](https://leetcode.com/problems/jump-game-vi)


## Description

<p>You are given a <strong>0-indexed</strong> integer array <code>nums</code> and an integer <code>k</code>.</p>

<p>You are initially standing at index <code>0</code>. In one move, you can jump at most <code>k</code> steps forward without going outside the boundaries of the array. That is, you can jump from index <code>i</code> to any index in the range <code>[i + 1, min(n - 1, i + k)]</code> <strong>inclusive</strong>.</p>

<p>You want to reach the last index of the array (index <code>n - 1</code>). Your <strong>score</strong> is the <strong>sum</strong> of all <code>nums[j]</code> for each index <code>j</code> you visited in the array.</p>

<p>Return <em>the <strong>maximum score</strong> you can get</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [<u>1</u>,<u>-1</u>,-2,<u>4</u>,-7,<u>3</u>], k = 2
<strong>Output:</strong> 7
<strong>Explanation:</strong> You can choose your jumps forming the subsequence [1,-1,4,3] (underlined above). The sum is 7.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [<u>10</u>,-5,-2,<u>4</u>,0,<u>3</u>], k = 3
<strong>Output:</strong> 17
<strong>Explanation:</strong> You can choose your jumps forming the subsequence [10,4,3] (underlined above). The sum is 17.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,-5,-20,4,-1,3,-6,-3], k = 2
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length, k &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
</ul>

## Solutions

### Solution 1: Dynamic Programming + Monotonic Queue Optimization

We define $f[i]$ as the maximum score when reaching index $i$. The value of $f[i]$ can be transferred from $f[j]$, where $j$ satisfies $i - k \leq j \leq i - 1$. Therefore, we can use dynamic programming to solve this problem.

The state transition equation is:

$$
f[i] = \max_{j \in [i - k, i - 1]} f[j] + nums[i]
$$

We can use a monotonic queue to optimize the state transition equation. Specifically, we maintain a monotonically decreasing queue, which stores the index $j$, and the $f[j]$ values corresponding to the indices in the queue are monotonically decreasing. When performing state transition, we only need to take out the index $j$ at the front of the queue to get the maximum value of $f[j]$, and then update the value of $f[i]$ to $f[j] + nums[i]$.

The time complexity is $O(n)$, and the space complexity is $O(n)$. Here, $n$ is the length of the array.

<!-- tabs:start -->

```python
class Solution:
    def maxResult(self, nums: List[int], k: int) -> int:
        n = len(nums)
        f = [0] * n
        q = deque([0])
        for i in range(n):
            if i - q[0] > k:
                q.popleft()
            f[i] = nums[i] + f[q[0]]
            while q and f[q[-1]] <= f[i]:
                q.pop()
            q.append(i)
        return f[-1]
```

```java
class Solution {
    public int maxResult(int[] nums, int k) {
        int n = nums.length;
        int[] f = new int[n];
        Deque<Integer> q = new ArrayDeque<>();
        q.offer(0);
        for (int i = 0; i < n; ++i) {
            if (i - q.peekFirst() > k) {
                q.pollFirst();
            }
            f[i] = nums[i] + f[q.peekFirst()];
            while (!q.isEmpty() && f[q.peekLast()] <= f[i]) {
                q.pollLast();
            }
            q.offerLast(i);
        }
        return f[n - 1];
    }
}
```

```cpp
class Solution {
public:
    int maxResult(vector<int>& nums, int k) {
        int n = nums.size();
        int f[n];
        f[0] = 0;
        deque<int> q = {0};
        for (int i = 0; i < n; ++i) {
            if (i - q.front() > k) q.pop_front();
            f[i] = nums[i] + f[q.front()];
            while (!q.empty() && f[q.back()] <= f[i]) q.pop_back();
            q.push_back(i);
        }
        return f[n - 1];
    }
};
```

```go
func maxResult(nums []int, k int) int {
	n := len(nums)
	f := make([]int, n)
	q := []int{0}
	for i, v := range nums {
		if i-q[0] > k {
			q = q[1:]
		}
		f[i] = v + f[q[0]]
		for len(q) > 0 && f[q[len(q)-1]] <= f[i] {
			q = q[:len(q)-1]
		}
		q = append(q, i)
	}
	return f[n-1]
}
```

<!-- tabs:end -->

<!-- end -->
