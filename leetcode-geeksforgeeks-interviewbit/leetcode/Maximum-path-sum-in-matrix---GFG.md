---
title: Maximum Path Sum In Matrix   Gfg
summary: Maximum Path Sum In Matrix   Gfg LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "Maximum path sum in matrix - GFG LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Maximum Path Sum In Matrix   Gfg - Solution Explained/problem-solving.webp
    alt: Maximum Path Sum In Matrix   Gfg
    hiddenInList: true
    hiddenInSingle: false
---


# Maximum path sum in matrix
## Medium
<div class="problems_problem_content__Xm_eO"><p><span style="font-size:18px">Given a NxN&nbsp;matrix&nbsp;of positive integers.&nbsp;There are only three possible moves from a cell <strong>Matrix[r][c]</strong>.</span></p>

<ol>
	<li><span style="font-size:18px">Matrix [r+1] [c]</span></li>
	<li><span style="font-size:18px">Matrix [r+1] [c-1]</span></li>
	<li><span style="font-size:18px">Matrix [r+1] [c+1]</span></li>
</ol>

<p><span style="font-size:18px">Starting from any column in row 0 return the largest sum of any of the paths up to row N-1.</span></p>

<p><span style="font-size:18px"><strong>NOTE:</strong> We can start from any column in zeroth row and can end at any column in (N-1)th row.</span><br>
<br>
<strong><span style="font-size:18px">Example 1:</span></strong></p>

<pre><span style="font-size:18px"><strong>Input:</strong> N = 2
<strong>Output:</strong> 1009
<strong>Explaination:</strong> The best path is 391 -&gt; 618. 
It gives the sum = 1009.</span></pre>

<p><br>
<strong><span style="font-size:18px">Example 2:</span></strong></p>

<pre><span style="font-size:18px"><strong>Input:</strong> N = 2
<strong>Output:</strong> 4
<strong>Explaination:</strong> No matter which path is 
chosen, the output is 4.</span></pre>

<p><br>
<span style="font-size:18px"><strong>Your Task:</strong><br>
You do not need to read input or print anything. Your task is to complete the function <strong>maximumPath() </strong>which takes the size N and the Matrix as input parameters and returns the highest maximum path sum.</span></p>

<p><br>
<span style="font-size:18px"><strong>Expected Time Complexity:</strong> O(N*N)<br>
<strong>Expected Auxiliary Space:</strong> O(N*N)</span></p>

<p><br>
<span style="font-size:18px"><strong>Constraints:</strong><br>
1 ≤ N ≤ 500<br>
1 ≤ Matrix[i][j] ≤ 1000</span></p>
</div>


---




```python
#User function Template for python3

class Solution:
    def maximumPath(self, N, Matrix):
        # code here
        for i in range(1, N):
            for j in range(N):
                if j == 0:
                    Matrix[i][j] += max(Matrix[i-1][j], Matrix[i-1][j+1])
                elif j == N-1:
                    Matrix[i][j] += max(Matrix[i-1][j-1], Matrix[i-1][j])
                else:
                    Matrix[i][j] += max(Matrix[i-1][j-1], Matrix[i-1][j], Matrix[i-1][j+1])
        
        return max(Matrix[-1])
        
        


#{ 
 # Driver Code Starts
#Initial Template for Python 3

if __name__ == '__main__': 
    t = int (input ())
    for _ in range (t):
        N = int(input())
        arr = input().split()
        Matrix = [[0]*N for i in range(N)]
        for itr in range(N*N):
            Matrix[(itr//N)][itr%N] = int(arr[itr])
        
        ob = Solution()
        print(ob.maximumPath(N, Matrix))

# } Driver Code Ends
```
