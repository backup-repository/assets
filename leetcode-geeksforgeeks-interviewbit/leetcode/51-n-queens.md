---
title: 51 N Queens
summary: 51 N Queens LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "51-n-queens LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:51 N Queens - Solution Explained/problem-solving.webp
    alt: 51 N Queens
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/n-queens/">51. N-Queens</a></h2><h3>Hard</h3><hr><div><p>The <strong>n-queens</strong> puzzle is the problem of placing <code>n</code> queens on an <code>n x n</code> chessboard such that no two queens attack each other.</p>

<p>Given an integer <code>n</code>, return <em>all distinct solutions to the <strong>n-queens puzzle</strong></em>. You may return the answer in <strong>any order</strong>.</p>

<p>Each solution contains a distinct board configuration of the n-queens' placement, where <code>'Q'</code> and <code>'.'</code> both indicate a queen and an empty space, respectively.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/13/queens.jpg" style="width: 600px; height: 268px;">
<pre><strong>Input:</strong> n = 4
<strong>Output:</strong> [[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
<strong>Explanation:</strong> There exist two distinct solutions to the 4-queens puzzle as shown above
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> n = 1
<strong>Output:</strong> [["Q"]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 9</code></li>
</ul>
</div>

---




```python
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        row = set()
        col = set()
        posDiag = set()
        negDiag = set()
        board = [['.']*n for i in range(n)]
        res = []
        
        def dfs(i):
            if i >= n: 
                s = ["".join(board[i]) for i in range(n)]
                res.append(s)
                return
            
            for j in range(n):
                if j in col or (i+j) in posDiag or (i-j) in negDiag: continue
                
                col.add(j)
                posDiag.add(i+j)
                negDiag.add(i-j)
                board[i][j] = "Q"

                dfs(i+1)

                col.remove(j)
                posDiag.remove(i+j)
                negDiag.remove(i-j)
                board[i][j] = "."
        
        dfs(0)
        return res

```
