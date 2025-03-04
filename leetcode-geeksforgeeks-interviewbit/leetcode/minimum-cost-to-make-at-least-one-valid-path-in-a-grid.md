---
title: Minimum Cost To Make At Least One Valid Path In A Grid
summary: Minimum Cost To Make At Least One Valid Path In A Grid LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "minimum-cost-to-make-at-least-one-valid-path-in-a-grid LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Minimum Cost To Make At Least One Valid Path In A Grid - Solution Explained/problem-solving.webp
    alt: Minimum Cost To Make At Least One Valid Path In A Grid
    hiddenInList: true
    hiddenInSingle: false
---


<h2>1368. Minimum Cost to Make at Least One Valid Path in a Grid</h2><h3>Hard</h3><hr><div>Given a <em>m</em> x <em>n</em> <code>grid</code>. Each cell of the <code>grid</code> has a sign pointing to the next cell you should visit if you are currently in this cell. The sign of <code>grid[i][j]</code> can be:
<ul>
	<li><strong>1</strong> which means go to the cell to the right. (i.e go from <code>grid[i][j]</code> to <code>grid[i][j + 1]</code>)</li>
	<li><strong>2</strong> which means go to the cell to the left. (i.e go from <code>grid[i][j]</code> to <code>grid[i][j - 1]</code>)</li>
	<li><strong>3</strong> which means go to the lower cell. (i.e go from <code>grid[i][j]</code> to <code>grid[i + 1][j]</code>)</li>
	<li><strong>4</strong> which means go to the upper cell. (i.e go from <code>grid[i][j]</code> to <code>grid[i - 1][j]</code>)</li>
</ul>

<p>Notice&nbsp;that there could be some <strong>invalid signs</strong> on the cells of the <code>grid</code> which points outside the <code>grid</code>.</p>

<p>You will initially start at the upper left cell <code>(0,0)</code>. A valid path in the grid is a path which starts from the upper left&nbsp;cell <code>(0,0)</code> and ends at the bottom-right&nbsp;cell <code>(m - 1, n - 1)</code> following the signs on the grid. The valid path <strong>doesn't have to be the shortest</strong>.</p>

<p>You can modify the sign on a cell with <code>cost = 1</code>. You can modify the sign on a cell <strong>one time only</strong>.</p>

<p>Return <em>the minimum cost</em> to make the grid have at least one valid path.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/02/13/grid1.png" style="width: 542px; height: 528px;">
<pre><strong>Input:</strong> grid = [[1,1,1,1],[2,2,2,2],[1,1,1,1],[2,2,2,2]]
<strong>Output:</strong> 3
<strong>Explanation:</strong> You will start at point (0, 0).
The path to (3, 3) is as follows. (0, 0) --&gt; (0, 1) --&gt; (0, 2) --&gt; (0, 3) change the arrow to down with cost = 1 --&gt; (1, 3) --&gt; (1, 2) --&gt; (1, 1) --&gt; (1, 0) change the arrow to down with cost = 1 --&gt; (2, 0) --&gt; (2, 1) --&gt; (2, 2) --&gt; (2, 3) change the arrow to down with cost = 1 --&gt; (3, 3)
The total cost = 3.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/02/13/grid2.png" style="width: 419px; height: 408px;">
<pre><strong>Input:</strong> grid = [[1,1,3],[3,2,2],[1,1,4]]
<strong>Output:</strong> 0
<strong>Explanation:</strong> You can follow the path from (0, 0) to (2, 2).
</pre>

<p><strong>Example 3:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/02/13/grid3.png" style="width: 314px; height: 302px;">
<pre><strong>Input:</strong> grid = [[1,2],[4,3]]
<strong>Output:</strong> 1
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> grid = [[2,2,2],[2,2,2]]
<strong>Output:</strong> 3
</pre>

<p><strong>Example 5:</strong></p>

<pre><strong>Input:</strong> grid = [[4]]
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 100</code></li>
</ul>
</div>

---




```cpp
class Solution {
public:
    int dx[4] = {0, 0, 1, -1};
    int dy[4] = {1, -1, 0, 0};
    
    int minCost(vector<vector<int>>& grid) {
        int m = grid.size(); 
        int n = grid[0].size();
       
        deque<pair<int, int>> dq;
        vector<int> dist(m*n, INT_MAX);
        
        int src = 0, des = m*n-1;
        
        dq.push_front({src, 0});
        dist[src] = 0;
                
        while(!dq.empty()) {
            int curr = dq.front().first;
            int dis = dq.front().second;
            
            dq.pop_front();
            
            if(curr == des)
                return dis;
            
            int x = curr/n , y = curr%n;
            
            for(int k=0; k<4; k++) {
                int i = x + dx[k];
                int j = y + dy[k];
                
                int u = i*n + j;
                
                if(i>=0 && j>=0 && i<m && j<n) {
                    int wt = (grid[x][y] != k+1);
                    
                    if(dis + wt < dist[u])
                    {
                        dist[u] = dis + wt;
                        if(wt == 1) 
                            dq.push_back({u, dis + wt});
                        else 
                            dq.push_front({u, dis + wt});
                    }
                }
            }
        }        
        return -1;
    }
};
```
