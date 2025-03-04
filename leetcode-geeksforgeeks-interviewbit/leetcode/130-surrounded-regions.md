---
title: 130 Surrounded Regions
summary: 130 Surrounded Regions LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "130-surrounded-regions LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:130 Surrounded Regions - Solution Explained/problem-solving.webp
    alt: 130 Surrounded Regions
    hiddenInList: true
    hiddenInSingle: false
---




---




```python
# https://leetcode.com/problems/surrounded-regions/
# https://youtu.be/0ZJViJEdtEc

''' 
Traverse the matrix boundary and whenever we get 'O' the call dfs from that call
and mark all connected 'O' to '.' 
Again traverse the matrix and and change 'O' to 'X' and '.' to 'O'
'''
class Solution:
    def solve(self, board: List[List[str]]) -> None:
        direc = [[1, 0], [-1, 0], [0, 1], [0, -1]]
        
        def dfs(i, j, val):
            if not 0<= i <len(board) or not 0 <= j < len(board[0]) or board[i][j] != 'O':
                return
            board[i][j] = val
            for k in range(4):
                r = i + direc[k][0]
                c = j + direc[k][1]
                dfs(r, c, val)

        # traverse the boundary
        for i in range(len(board)):
            for j in range(len(board[0])):
                if (i == len(board)-1 or i == 0 or j == len(board[0])-1 or j == 0) and board[i][j] == 'O':
                    dfs(i, j, '.')
        
        # Traverse the whole matrix to change 'O' to 'X' and '.' to 'O' 
        for i in range(len(board)):
            for j in range(len(board[0])):
                if board[i][j] == 'O':
                    board[i][j] = 'X'
                elif board[i][j] == '.':
                    board[i][j] = 'O'
        
        return board

# Time: O(m * n)
# Space: O(1)
```
