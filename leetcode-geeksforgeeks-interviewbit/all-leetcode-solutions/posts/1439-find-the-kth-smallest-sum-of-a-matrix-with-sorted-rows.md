---
title: 1439 Find The Kth Smallest Sum Of A Matrix With Sorted Rows
summary: 1439 Find The Kth Smallest Sum Of A Matrix With Sorted Rows LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1439 Find The Kth Smallest Sum Of A Matrix With Sorted Rows LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1439 Find The Kth Smallest Sum Of A Matrix With Sorted Rows - Solution Explained/problem-solving.webp
    alt: 1439 Find The Kth Smallest Sum Of A Matrix With Sorted Rows
    hiddenInList: true
    hiddenInSingle: false
---


# [1439. Find the Kth Smallest Sum of a Matrix With Sorted Rows](https://leetcode.com/problems/find-the-kth-smallest-sum-of-a-matrix-with-sorted-rows)


## Description

<p>You are given an <code>m x n</code> matrix <code>mat</code> that has its rows sorted in non-decreasing order and an integer <code>k</code>.</p>

<p>You are allowed to choose <strong>exactly one element</strong> from each row to form an array.</p>

<p>Return <em>the </em><code>k<sup>th</sup></code><em> smallest array sum among all possible arrays</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> mat = [[1,3,11],[2,4,6]], k = 5
<strong>Output:</strong> 7
<strong>Explanation:</strong> Choosing one element from each row, the first k smallest sum are:
[1,2], [1,4], [3,2], [3,4], [1,6]. Where the 5th sum is 7.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> mat = [[1,3,11],[2,4,6]], k = 9
<strong>Output:</strong> 17
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> mat = [[1,10,10],[1,4,5],[2,3,6]], k = 7
<strong>Output:</strong> 9
<strong>Explanation:</strong> Choosing one element from each row, the first k smallest sum are:
[1,1,2], [1,1,3], [1,4,2], [1,4,3], [1,1,6], [1,5,2], [1,5,3]. Where the 7th sum is 9.  
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == mat.length</code></li>
	<li><code>n == mat.length[i]</code></li>
	<li><code>1 &lt;= m, n &lt;= 40</code></li>
	<li><code>1 &lt;= mat[i][j] &lt;= 5000</code></li>
	<li><code>1 &lt;= k &lt;= min(200, n<sup>m</sup>)</code></li>
	<li><code>mat[i]</code> is a non-decreasing array.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def kthSmallest(self, mat: List[List[int]], k: int) -> int:
        pre = [0]
        for cur in mat:
            pre = sorted(a + b for a in pre for b in cur[:k])[:k]
        return pre[-1]
```

```java
class Solution {
    public int kthSmallest(int[][] mat, int k) {
        int m = mat.length, n = mat[0].length;
        List<Integer> pre = new ArrayList<>(k);
        List<Integer> cur = new ArrayList<>(n * k);
        pre.add(0);
        for (int[] row : mat) {
            cur.clear();
            for (int a : pre) {
                for (int b : row) {
                    cur.add(a + b);
                }
            }
            Collections.sort(cur);
            pre.clear();
            for (int i = 0; i < Math.min(k, cur.size()); ++i) {
                pre.add(cur.get(i));
            }
        }
        return pre.get(k - 1);
    }
}
```

```cpp
class Solution {
public:
    int kthSmallest(vector<vector<int>>& mat, int k) {
        int pre[k];
        int cur[mat[0].size() * k];
        memset(pre, 0, sizeof pre);
        int size = 1;
        for (auto& row : mat) {
            int i = 0;
            for (int j = 0; j < size; ++j) {
                for (int& v : row) {
                    cur[i++] = pre[j] + v;
                }
            }
            sort(cur, cur + i);
            size = min(i, k);
            for (int j = 0; j < size; ++j) {
                pre[j] = cur[j];
            }
        }
        return pre[k - 1];
    }
};
```

```go
func kthSmallest(mat [][]int, k int) int {
	pre := []int{0}
	for _, row := range mat {
		cur := []int{}
		for _, a := range pre {
			for _, b := range row {
				cur = append(cur, a+b)
			}
		}
		sort.Ints(cur)
		pre = cur[:min(k, len(cur))]
	}
	return pre[k-1]
}
```

```ts
function kthSmallest(mat: number[][], k: number): number {
    let pre: number[] = [0];
    for (const cur of mat) {
        const next: number[] = [];
        for (const a of pre) {
            for (const b of cur) {
                next.push(a + b);
            }
        }
        pre = next.sort((a, b) => a - b).slice(0, k);
    }
    return pre[k - 1];
}
```

<!-- tabs:end -->

<!-- end -->
