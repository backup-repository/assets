---
title: 2257 Count Unguarded Cells In The Grid
summary: 2257 Count Unguarded Cells In The Grid LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "2257 Count Unguarded Cells In The Grid LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2257 Count Unguarded Cells In The Grid - Solution Explained/problem-solving.webp
    alt: 2257 Count Unguarded Cells In The Grid
    hiddenInList: true
    hiddenInSingle: false
---


# [2257. Count Unguarded Cells in the Grid](https://leetcode.com/problems/count-unguarded-cells-in-the-grid)


## Description

<p>You are given two integers <code>m</code> and <code>n</code> representing a <strong>0-indexed</strong> <code>m x n</code> grid. You are also given two 2D integer arrays <code>guards</code> and <code>walls</code> where <code>guards[i] = [row<sub>i</sub>, col<sub>i</sub>]</code> and <code>walls[j] = [row<sub>j</sub>, col<sub>j</sub>]</code> represent the positions of the <code>i<sup>th</sup></code> guard and <code>j<sup>th</sup></code> wall respectively.</p>

<p>A guard can see <b>every</b> cell in the four cardinal directions (north, east, south, or west) starting from their position unless <strong>obstructed</strong> by a wall or another guard. A cell is <strong>guarded</strong> if there is <strong>at least</strong> one guard that can see it.</p>

<p>Return<em> the number of unoccupied cells that are <strong>not</strong> <strong>guarded</strong>.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/solution/2200-2299/2257.Count%20Unguarded%20Cells%20in%20the%20Grid/images/example1drawio2.png" style="width: 300px; height: 204px;" />
<pre>
<strong>Input:</strong> m = 4, n = 6, guards = [[0,0],[1,1],[2,3]], walls = [[0,1],[2,2],[1,4]]
<strong>Output:</strong> 7
<strong>Explanation:</strong> The guarded and unguarded cells are shown in red and green respectively in the above diagram.
There are a total of 7 unguarded cells, so we return 7.
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/solution/2200-2299/2257.Count%20Unguarded%20Cells%20in%20the%20Grid/images/example2drawio.png" style="width: 200px; height: 201px;" />
<pre>
<strong>Input:</strong> m = 3, n = 3, guards = [[1,1]], walls = [[0,1],[1,0],[2,1],[1,2]]
<strong>Output:</strong> 4
<strong>Explanation:</strong> The unguarded cells are shown in green in the above diagram.
There are a total of 4 unguarded cells, so we return 4.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= m, n &lt;= 10<sup>5</sup></code></li>
	<li><code>2 &lt;= m * n &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= guards.length, walls.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>2 &lt;= guards.length + walls.length &lt;= m * n</code></li>
	<li><code>guards[i].length == walls[j].length == 2</code></li>
	<li><code>0 &lt;= row<sub>i</sub>, row<sub>j</sub> &lt; m</code></li>
	<li><code>0 &lt;= col<sub>i</sub>, col<sub>j</sub> &lt; n</code></li>
	<li>All the positions in <code>guards</code> and <code>walls</code> are <strong>unique</strong>.</li>
</ul>

## Solutions

### Solution 1: Simulation

We create a two-dimensional array $g$ of size $m \times n$, where $g[i][j]$ represents the cell in row $i$ and column $j$. Initially, the value of $g[i][j]$ is $0$, indicating that the cell is not guarded.

Then, we traverse all guards and walls, and set the value of $g[i][j]$ to $2$, indicating that these positions cannot be accessed.

Next, we traverse all guard positions, simulate in four directions from that position until we encounter a wall or guard, or go out of bounds. During the simulation, we set the value of the encountered cell to $1$, indicating that the cell is guarded.

Finally, we traverse $g$ and count the number of cells with a value of $0$, which is the answer.

The time complexity is $O(m \times n)$, and the space complexity is $O(m \times n)$. Here, $m$ and $n$ are the number of rows and columns in the grid, respectively.

<!-- tabs:start -->

```python
class Solution:
    def countUnguarded(
        self, m: int, n: int, guards: List[List[int]], walls: List[List[int]]
    ) -> int:
        g = [[0] * n for _ in range(m)]
        for i, j in guards:
            g[i][j] = 2
        for i, j in walls:
            g[i][j] = 2
        dirs = (-1, 0, 1, 0, -1)
        for i, j in guards:
            for a, b in pairwise(dirs):
                x, y = i, j
                while 0 <= x + a < m and 0 <= y + b < n and g[x + a][y + b] < 2:
                    x, y = x + a, y + b
                    g[x][y] = 1
        return sum(v == 0 for row in g for v in row)
```

```java
class Solution {
    public int countUnguarded(int m, int n, int[][] guards, int[][] walls) {
        int[][] g = new int[m][n];
        for (var e : guards) {
            g[e[0]][e[1]] = 2;
        }
        for (var e : walls) {
            g[e[0]][e[1]] = 2;
        }
        int[] dirs = {-1, 0, 1, 0, -1};
        for (var e : guards) {
            for (int k = 0; k < 4; ++k) {
                int x = e[0], y = e[1];
                int a = dirs[k], b = dirs[k + 1];
                while (x + a >= 0 && x + a < m && y + b >= 0 && y + b < n && g[x + a][y + b] < 2) {
                    x += a;
                    y += b;
                    g[x][y] = 1;
                }
            }
        }
        int ans = 0;
        for (var row : g) {
            for (int v : row) {
                if (v == 0) {
                    ++ans;
                }
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int countUnguarded(int m, int n, vector<vector<int>>& guards, vector<vector<int>>& walls) {
        int g[m][n];
        memset(g, 0, sizeof(g));
        for (auto& e : guards) {
            g[e[0]][e[1]] = 2;
        }
        for (auto& e : walls) {
            g[e[0]][e[1]] = 2;
        }
        int dirs[5] = {-1, 0, 1, 0, -1};
        for (auto& e : guards) {
            for (int k = 0; k < 4; ++k) {
                int x = e[0], y = e[1];
                int a = dirs[k], b = dirs[k + 1];
                while (x + a >= 0 && x + a < m && y + b >= 0 && y + b < n && g[x + a][y + b] < 2) {
                    x += a;
                    y += b;
                    g[x][y] = 1;
                }
            }
        }
        int ans = 0;
        for (auto& row : g) {
            ans += count(row, row + n, 0);
        }
        return ans;
    }
};
```

```go
func countUnguarded(m int, n int, guards [][]int, walls [][]int) (ans int) {
	g := make([][]int, m)
	for i := range g {
		g[i] = make([]int, n)
	}
	for _, e := range guards {
		g[e[0]][e[1]] = 2
	}
	for _, e := range walls {
		g[e[0]][e[1]] = 2
	}
	dirs := [5]int{-1, 0, 1, 0, -1}
	for _, e := range guards {
		for k := 0; k < 4; k++ {
			x, y := e[0], e[1]
			a, b := dirs[k], dirs[k+1]
			for x+a >= 0 && x+a < m && y+b >= 0 && y+b < n && g[x+a][y+b] < 2 {
				x, y = x+a, y+b
				g[x][y] = 1
			}
		}
	}
	for _, row := range g {
		for _, v := range row {
			if v == 0 {
				ans++
			}
		}
	}
	return
}
```

```ts
function countUnguarded(m: number, n: number, guards: number[][], walls: number[][]): number {
    const g: number[][] = Array.from({ length: m }, () => Array.from({ length: n }, () => 0));
    for (const [i, j] of guards) {
        g[i][j] = 2;
    }
    for (const [i, j] of walls) {
        g[i][j] = 2;
    }
    const dirs: number[] = [-1, 0, 1, 0, -1];
    for (const [i, j] of guards) {
        for (let k = 0; k < 4; ++k) {
            let [x, y] = [i, j];
            let [a, b] = [dirs[k], dirs[k + 1]];
            while (x + a >= 0 && x + a < m && y + b >= 0 && y + b < n && g[x + a][y + b] < 2) {
                x += a;
                y += b;
                g[x][y] = 1;
            }
        }
    }
    let ans = 0;
    for (const row of g) {
        for (const v of row) {
            ans += v === 0 ? 1 : 0;
        }
    }
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
