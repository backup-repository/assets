---
title: Longest Consecutive Sequence
summary: Longest Consecutive Sequence LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "longest-consecutive-sequence LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Longest Consecutive Sequence - Solution Explained/problem-solving.webp
    alt: Longest Consecutive Sequence
    hiddenInList: true
    hiddenInSingle: false
---


<h2>128. Longest Consecutive Sequence</h2><h3>Medium</h3><hr><div><p>Given an unsorted array of integers <code>nums</code>, return <em>the length of the longest consecutive elements sequence.</em></p>

<p>You must write an algorithm that runs in&nbsp;<code>O(n)</code>&nbsp;time.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [100,4,200,1,3,2]
<strong>Output:</strong> 4
<strong>Explanation:</strong> The longest consecutive elements sequence is <code>[1, 2, 3, 4]</code>. Therefore its length is 4.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [0,3,7,2,5,8,4,6,0,1]
<strong>Output:</strong> 9
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
</ul>
</div>

---




```cpp
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        int n=nums.size();
        map<int, int> m;
        int ans=0;
        for(auto x: nums)
            m[x]++;
        for(auto x: m){ // x is start of streak
            if(!m.count(x.first-1)){ 
                int curr=x.first;
                int maxsf=1;
                while(m.find(curr+1)!=m.end()){
                    curr++;
                    maxsf++;
                }
            ans=max(ans, maxsf);
            }
        }
        return ans;
    }
};
```
