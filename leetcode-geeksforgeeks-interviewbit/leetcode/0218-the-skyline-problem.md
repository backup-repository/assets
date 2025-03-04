---
title: 0218 The Skyline Problem
summary: 0218 The Skyline Problem LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "0218-the-skyline-problem LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0218 The Skyline Problem - Solution Explained/problem-solving.webp
    alt: 0218 The Skyline Problem
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/the-skyline-problem/">218. The Skyline Problem</a></h2><h3>Hard</h3><hr><div><p>A city's <strong>skyline</strong> is the outer contour of the silhouette formed by all the buildings in that city when viewed from a distance. Given the locations and heights of all the buildings, return <em>the <strong>skyline</strong> formed by these buildings collectively</em>.</p>

<p>The geometric information of each building is given in the array <code>buildings</code> where <code>buildings[i] = [left<sub>i</sub>, right<sub>i</sub>, height<sub>i</sub>]</code>:</p>

<ul>
	<li><code>left<sub>i</sub></code> is the x coordinate of the left edge of the <code>i<sup>th</sup></code> building.</li>
	<li><code>right<sub>i</sub></code> is the x coordinate of the right edge of the <code>i<sup>th</sup></code> building.</li>
	<li><code>height<sub>i</sub></code> is the height of the <code>i<sup>th</sup></code> building.</li>
</ul>

<p>You may assume all buildings are perfect rectangles grounded on an absolutely flat surface at height <code>0</code>.</p>

<p>The <strong>skyline</strong> should be represented as a list of "key points" <strong>sorted by their x-coordinate</strong> in the form <code>[[x<sub>1</sub>,y<sub>1</sub>],[x<sub>2</sub>,y<sub>2</sub>],...]</code>. Each key point is the left endpoint of some horizontal segment in the skyline except the last point in the list, which always has a y-coordinate <code>0</code> and is used to mark the skyline's termination where the rightmost building ends. Any ground between the leftmost and rightmost buildings should be part of the skyline's contour.</p>

<p><b>Note:</b> There must be no consecutive horizontal lines of equal height in the output skyline. For instance, <code>[...,[2 3],[4 5],[7 5],[11 5],[12 7],...]</code> is not acceptable; the three lines of height 5 should be merged into one in the final output as such: <code>[...,[2 3],[4 5],[12 7],...]</code></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/12/01/merged.jpg" style="width: 800px; height: 331px;">
<pre><strong>Input:</strong> buildings = [[2,9,10],[3,7,15],[5,12,12],[15,20,10],[19,24,8]]
<strong>Output:</strong> [[2,10],[3,15],[7,12],[12,0],[15,10],[20,8],[24,0]]
<strong>Explanation:</strong>
Figure A shows the buildings of the input.
Figure B shows the skyline formed by those buildings. The red points in figure B represent the key points in the output list.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> buildings = [[0,2,3],[2,5,3]]
<strong>Output:</strong> [[0,3],[5,0]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= buildings.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= left<sub>i</sub> &lt; right<sub>i</sub> &lt;= 2<sup>31</sup> - 1</code></li>
	<li><code>1 &lt;= height<sub>i</sub> &lt;= 2<sup>31</sup> - 1</code></li>
	<li><code>buildings</code> is sorted by <code>left<sub>i</sub></code> in&nbsp;non-decreasing order.</li>
</ul>
</div>

---




```python
# https://leetcode.com/problems/the-skyline-problem/
# https://youtu.be/POUMNJou4vc

import heapq
class Solution:
    def getSkyline(self, buildings):
        corners = []
        for l, r, h in buildings:
            corners.append((l, -h))
            corners.append((r, h))
        corners.sort()
        print(corners)
        # as heapq does not support delete element by value. 
        removed = collections.Counter()
        maxHeap = [0]
        res = []
        
        def getMaxHeight():
            mh = - maxHeap[0]  # max height
            while mh in removed:
                removed[mh] -= 1
                if removed[mh] == 0: del removed[mh]
                heapq.heappop(maxHeap)
                mh = - maxHeap[0]
            return mh
        
        for x, y in corners:
            mh = getMaxHeight()
            if y < 0:
                if -y > mh:
                    res.append([x, -y])
                heapq.heappush(maxHeap, y)
            else:
                ph = mh
                removed[y] += 1
                if y == mh:
                    mh = getMaxHeight()
                    if ph > mh: res.append([x, mh])
        
        return res
```
