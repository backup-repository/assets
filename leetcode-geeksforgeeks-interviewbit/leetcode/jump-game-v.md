---
title: Jump Game V
summary: Jump Game V LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "jump-game-v LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Jump Game V - Solution Explained/problem-solving.webp
    alt: Jump Game V
    hiddenInList: true
    hiddenInSingle: false
---


<h2>1340. Jump Game V</h2><h3>Hard</h3><hr><div><p>Given an array of&nbsp;integers <code>arr</code> and an integer <code>d</code>. In one step you can jump from index <code>i</code> to index:</p>

<ul>
	<li><code>i + x</code> where:&nbsp;<code>i + x &lt; arr.length</code> and <code> 0 &lt;&nbsp;x &lt;= d</code>.</li>
	<li><code>i - x</code> where:&nbsp;<code>i - x &gt;= 0</code> and <code> 0 &lt;&nbsp;x &lt;= d</code>.</li>
</ul>

<p>In addition, you can only jump from index <code>i</code> to index <code>j</code>&nbsp;if <code>arr[i] &gt; arr[j]</code> and <code>arr[i] &gt; arr[k]</code> for all indices <code>k</code> between <code>i</code> and <code>j</code> (More formally <code>min(i,&nbsp;j) &lt; k &lt; max(i, j)</code>).</p>

<p>You can choose any index of the array and start jumping. Return <em>the maximum number of indices</em>&nbsp;you can visit.</p>

<p>Notice that you can not jump outside of the array at any time.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/01/23/meta-chart.jpeg" style="width: 633px; height: 419px;">
<pre><strong>Input:</strong> arr = [6,4,14,6,8,13,9,7,10,6,12], d = 2
<strong>Output:</strong> 4
<strong>Explanation:</strong> You can start at index 10. You can jump 10 --&gt; 8 --&gt; 6 --&gt; 7 as shown.
Note that if you start at index 6 you can only jump to index 7. You cannot jump to index 5 because 13 &gt; 9. You cannot jump to index 4 because index 5 is between index 4 and 6 and 13 &gt; 9.
Similarly You cannot jump from index 3 to index 2 or index 1.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> arr = [3,3,3,3,3], d = 3
<strong>Output:</strong> 1
<strong>Explanation:</strong> You can start at any index. You always cannot jump to any index.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> arr = [7,6,5,4,3,2,1], d = 1
<strong>Output:</strong> 7
<strong>Explanation:</strong> Start at index 0. You can visit all the indicies. 
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> arr = [7,1,7,1,7,1], d = 2
<strong>Output:</strong> 2
</pre>

<p><strong>Example 5:</strong></p>

<pre><strong>Input:</strong> arr = [66], d = 1
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 1000</code></li>
	<li><code>1 &lt;= arr[i] &lt;= 10^5</code></li>
	<li><code>1 &lt;= d &lt;= arr.length</code></li>
</ul></div>

---




```cpp
class Solution {
public:
    int dp[1000001];
    int n;
    int solve(int i,vector<int>& arr, int d){
        if(dp[i]!=-1)
            return dp[i];
        dp[i]=0;
        for(int k=i+1;k<n && k<=i+d && arr[k]<arr[i]; k++)
            dp[i]=max(dp[i], 1+solve(k, arr,d));
        for(int k=i-1;k>=0 && k>=i-d && arr[k]<arr[i]; k--)
            dp[i]=max(dp[i], 1+solve(k, arr,d));
        return dp[i];
    }
    
    int maxJumps(vector<int>& arr, int d) {
        n=arr.size();
        int ans=0;
        for(int i=0;i<1001;i++)
            dp[i]=-1;
        for(int i=0;i<n;i++)
            ans=max(ans, 1+solve(i,arr,d));
        return ans;
    }
};
```
