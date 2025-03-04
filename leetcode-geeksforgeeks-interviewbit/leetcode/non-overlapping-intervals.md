---
title: Non Overlapping Intervals
summary: Non Overlapping Intervals LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "non-overlapping-intervals LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Non Overlapping Intervals - Solution Explained/problem-solving.webp
    alt: Non Overlapping Intervals
    hiddenInList: true
    hiddenInSingle: false
---


<h2>435. Non-overlapping Intervals</h2><h3>Medium</h3><hr><div><p>Given a collection of intervals, find the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping.</p>

<ol>
</ol>

<p>&nbsp;</p>

<p><b>Example 1:</b></p>

<pre><b>Input:</b> [[1,2],[2,3],[3,4],[1,3]]
<b>Output:</b> 1
<b>Explanation:</b> [1,3] can be removed and the rest of intervals are non-overlapping.
</pre>

<p><b>Example 2:</b></p>

<pre><b>Input:</b> [[1,2],[1,2],[1,2]]
<b>Output:</b> 2
<b>Explanation:</b> You need to remove two [1,2] to make the rest of intervals non-overlapping.
</pre>

<p><b>Example 3:</b></p>

<pre><b>Input:</b> [[1,2],[2,3]]
<b>Output:</b> 0
<b>Explanation:</b> You don't need to remove any of the intervals since they're already non-overlapping.
</pre>

<p>&nbsp;</p>

<p><b>Note:</b></p>

<ol>
	<li>You may assume the interval's end point is always bigger than its start point.</li>
	<li>Intervals like [1,2] and [2,3] have borders "touching" but they don't overlap each other.</li>
</ol>
</div>

---




```cpp
class Solution {
public:
  
    static bool comp(vector<int> &a, vector<int> &b){
        return a[1]<b[1];
    }
    
    int eraseOverlapIntervals(vector<vector<int>>& intervals) {
        if(intervals.size()==0)
            return 0;
        sort(intervals.begin(),intervals.end(), comp);
        int ans=0;
        vector<int> prev=intervals[0];
        for(int i=1;i<intervals.size();i++){
            if(intervals[i][0]<prev[1])
                ans++;
            else
                prev=intervals[i];
        }
        return ans;
    }
};

```
