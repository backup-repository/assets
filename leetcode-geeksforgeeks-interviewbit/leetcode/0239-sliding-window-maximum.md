---
title: 0239 Sliding Window Maximum
summary: 0239 Sliding Window Maximum LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "0239-sliding-window-maximum LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0239 Sliding Window Maximum - Solution Explained/problem-solving.webp
    alt: 0239 Sliding Window Maximum
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/sliding-window-maximum/">239. Sliding Window Maximum</a></h2><h3>Hard</h3><hr><div><p>You are given an array of integers&nbsp;<code>nums</code>, there is a sliding window of size <code>k</code> which is moving from the very left of the array to the very right. You can only see the <code>k</code> numbers in the window. Each time the sliding window moves right by one position.</p>

<p>Return <em>the max sliding window</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [1,3,-1,-3,5,3,6,7], k = 3
<strong>Output:</strong> [3,3,5,5,6,7]
<strong>Explanation:</strong> 
Window position                Max
---------------               -----
[1  3  -1] -3  5  3  6  7       <strong>3</strong>
 1 [3  -1  -3] 5  3  6  7       <strong>3</strong>
 1  3 [-1  -3  5] 3  6  7      <strong> 5</strong>
 1  3  -1 [-3  5  3] 6  7       <strong>5</strong>
 1  3  -1  -3 [5  3  6] 7       <strong>6</strong>
 1  3  -1  -3  5 [3  6  7]      <strong>7</strong>
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [1], k = 1
<strong>Output:</strong> [1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= k &lt;= nums.length</code></li>
</ul>
</div>

---




```python
### Solution 1 # Using Queue
class Solution:
    def maxSlidingWindow(self, nums, k):
        q = collections.deque()
        res = []
        
        for i, ch in enumerate(nums):
            while q and nums[q[-1]] <= ch:
                q.pop()
            if q and i - q[0] >= k:
                q.popleft()
            q.append(i)
            if i >= k-1: res.append(nums[q[0]])
        
        return res
    
    
### Solution 2 # Using MaxHeap
import heapq
class Solution:
    def maxSlidingWindow(self, nums, k):
        maxHeap = []
        res = []
        l = r = 0
        for r, ch in enumerate(nums):
            heapq.heappush(maxHeap, (-ch, r))
            if r-l+1 > k: l += 1
            while maxHeap and maxHeap[0][1] < l:
                heapq.heappop(maxHeap)
            if r >= k-1 and maxHeap:
                res.append(-maxHeap[0][0])
        
        return res
```
