---
title: Cherry Pickup
summary: Cherry Pickup LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "cherry-pickup LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Cherry Pickup - Solution Explained/problem-solving.webp
    alt: Cherry Pickup
    hiddenInList: true
    hiddenInSingle: false
---


<h2>741. Cherry Pickup</h2><h3>Hard</h3><hr><div><p>You are given an <code>n x n</code> <code>grid</code> representing a field of cherries, each cell is one of three possible integers.</p>

<ul>
	<li><code>0</code> means the cell is empty, so you can pass through,</li>
	<li><code>1</code> means the cell contains a cherry that you can pick up and pass through, or</li>
	<li><code>-1</code> means the cell contains a thorn that blocks your way.</li>
</ul>

<p>Return <em>the maximum number of cherries you can collect by following the rules below</em>:</p>

<ul>
	<li>Starting at the position <code>(0, 0)</code> and reaching <code>(n - 1, n - 1)</code> by moving right or down through valid path cells (cells with value <code>0</code> or <code>1</code>).</li>
	<li>After reaching <code>(n - 1, n - 1)</code>, returning to <code>(0, 0)</code> by moving left or up through valid path cells.</li>
	<li>When passing through a path cell containing a cherry, you pick it up, and the cell becomes an empty cell <code>0</code>.</li>
	<li>If there is no valid path between <code>(0, 0)</code> and <code>(n - 1, n - 1)</code>, then no cherries can be collected.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/12/14/grid.jpg" style="width: 242px; height: 242px;">
<pre><strong>Input:</strong> grid = [[0,1,-1],[1,0,-1],[1,1,1]]
<strong>Output:</strong> 5
<strong>Explanation:</strong> The player started at (0, 0) and went down, down, right right to reach (2, 2).
4 cherries were picked up during this single trip, and the matrix becomes [[0,1,-1],[0,0,-1],[0,0,0]].
Then, the player went left, up, up, left to return home, picking up one more cherry.
The total number of cherries picked up is 5, and this is the maximum possible.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> grid = [[1,1,-1],[1,-1,1],[-1,1,1]]
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= n &lt;= 50</code></li>
	<li><code>grid[i][j]</code> is <code>-1</code>, <code>0</code>, or <code>1</code>.</li>
	<li><code>grid[0][0] != -1</code></li>
	<li><code>grid[n - 1][n - 1] != -1</code></li>
</ul>
</div>

---




```cpp
class Solution {
public:
    int t[51][51][51];
    vector<vector<int>> g;
    
    int solve(int r1, int c1, int c2, int n){
        int r2=r1+c1-c2;
        if(r1>=n || r2>=n || c1>=n || c2>=n || g[r1][c1]==-1 || g[r2][c2]==-1)
            return INT_MIN;
        if(t[r1][c1][c2]!=-1)
            return t[r1][c1][c2];
        if(r1==n-1 && c1==n-1)
            return g[r1][c1];
        int ans=g[r1][c1];
        if(c1!=c2)
            ans+=g[r2][c2];
        ans+=max(max(solve(r1,c1+1,c2+1,n), solve(r1+1,c1,c2+1,n)), max(solve(r1,c1+1,c2,n), solve(r1+1,c1,c2,n)));
        return t[r1][c1][c2]=ans;
        
    }
    
    
    
    int cherryPickup(vector<vector<int>>& grid) {
        int n=grid.size();
        g=grid;
        memset(t,-1,sizeof(t));
        return max(0,solve(0,0,0,n));
    }
};

```
