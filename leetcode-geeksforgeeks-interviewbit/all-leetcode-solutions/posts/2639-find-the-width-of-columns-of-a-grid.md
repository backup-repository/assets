---
title: 2639 Find The Width Of Columns Of A Grid
summary: 2639 Find The Width Of Columns Of A Grid LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "2639 Find The Width Of Columns Of A Grid LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2639 Find The Width Of Columns Of A Grid - Solution Explained/problem-solving.webp
    alt: 2639 Find The Width Of Columns Of A Grid
    hiddenInList: true
    hiddenInSingle: false
---


# [2639. Find the Width of Columns of a Grid](https://leetcode.com/problems/find-the-width-of-columns-of-a-grid)


## Description

<p>You are given a <strong>0-indexed</strong> <code>m x n</code> integer matrix <code>grid</code>. The width of a column is the maximum <strong>length </strong>of its integers.</p>

<ul>
	<li>For example, if <code>grid = [[-10], [3], [12]]</code>, the width of the only column is <code>3</code> since <code>-10</code> is of length <code>3</code>.</li>
</ul>

<p>Return <em>an integer array</em> <code>ans</code> <em>of size</em> <code>n</code> <em>where</em> <code>ans[i]</code> <em>is the width of the</em> <code>i<sup>th</sup></code> <em>column</em>.</p>

<p>The <strong>length</strong> of an integer <code>x</code> with <code>len</code> digits is equal to <code>len</code> if <code>x</code> is non-negative, and <code>len + 1</code> otherwise.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> grid = [[1],[22],[333]]
<strong>Output:</strong> [3]
<strong>Explanation:</strong> In the 0<sup>th</sup> column, 333 is of length 3.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> grid = [[-15,1,3],[15,7,12],[5,6,-2]]
<strong>Output:</strong> [3,1,2]
<strong>Explanation:</strong> 
In the 0<sup>th</sup> column, only -15 is of length 3.
In the 1<sup>st</sup> column, all integers are of length 1. 
In the 2<sup>nd</sup> column, both 12 and -2 are of length 2.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 100 </code></li>
	<li><code>-10<sup>9</sup> &lt;= grid[r][c] &lt;= 10<sup>9</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def findColumnWidth(self, grid: List[List[int]]) -> List[int]:
        ans = [0] * len(grid[0])
        for row in grid:
            for j, x in enumerate(row):
                w = len(str(x))
                ans[j] = max(ans[j], w)
        return ans
```

```java
class Solution {
    public int[] findColumnWidth(int[][] grid) {
        int n = grid[0].length;
        int[] ans = new int[n];
        for (var row : grid) {
            for (int j = 0; j < n; ++j) {
                int w = String.valueOf(row[j]).length();
                ans[j] = Math.max(ans[j], w);
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    vector<int> findColumnWidth(vector<vector<int>>& grid) {
        int n = grid[0].size();
        vector<int> ans(n);
        for (auto& row : grid) {
            for (int j = 0; j < n; ++j) {
                int w = to_string(row[j]).size();
                ans[j] = max(ans[j], w);
            }
        }
        return ans;
    }
};
```

```go
func findColumnWidth(grid [][]int) []int {
	ans := make([]int, len(grid[0]))
	for _, row := range grid {
		for j, x := range row {
			w := len(strconv.Itoa(x))
			ans[j] = max(ans[j], w)
		}
	}
	return ans
}
```

```ts
function findColumnWidth(grid: number[][]): number[] {
    const n = grid[0].length;
    const ans: number[] = new Array(n).fill(0);
    for (const row of grid) {
        for (let j = 0; j < n; ++j) {
            const w: number = String(row[j]).length;
            ans[j] = Math.max(ans[j], w);
        }
    }
    return ans;
}
```

```rust
impl Solution {
    pub fn find_column_width(grid: Vec<Vec<i32>>) -> Vec<i32> {
        let mut ans = vec![0; grid[0].len()];

        for row in grid.iter() {
            for (j, num) in row.iter().enumerate() {
                let width = num.to_string().len() as i32;
                ans[j] = std::cmp::max(ans[j], width);
            }
        }

        ans
    }
}
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```python
class Solution:
    def findColumnWidth(self, grid: List[List[int]]) -> List[int]:
        return [max(len(str(x)) for x in col) for col in zip(*grid)]
```

<!-- tabs:end -->

<!-- end -->
