---
title: Reduce Array Size To The Half
summary: Reduce Array Size To The Half LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "reduce-array-size-to-the-half LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Reduce Array Size To The Half - Solution Explained/problem-solving.webp
    alt: Reduce Array Size To The Half
    hiddenInList: true
    hiddenInSingle: false
---


<h2>1338. Reduce Array Size to The Half</h2><h3>Medium</h3><hr><div><p>Given an array <code>arr</code>.&nbsp; You can choose a set of integers and remove all the occurrences of these integers in the array.</p>

<p>Return <em>the minimum size of the set</em> so that <strong>at least</strong> half of the integers of the array are removed.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> arr = [3,3,3,3,5,5,5,2,2,7]
<strong>Output:</strong> 2
<strong>Explanation:</strong> Choosing {3,7} will make the new array [5,5,5,2,2] which has size 5 (i.e equal to half of the size of the old array).
Possible sets of size 2 are {3,5},{3,2},{5,2}.
Choosing set {2,7} is not possible as it will make the new array [3,3,3,3,5,5,5] which has size greater than half of the size of the old array.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> arr = [7,7,7,7,7,7]
<strong>Output:</strong> 1
<strong>Explanation:</strong> The only possible set you can choose is {7}. This will make the new array empty.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> arr = [1,9]
<strong>Output:</strong> 1
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> arr = [1000,1000,3,7]
<strong>Output:</strong> 1
</pre>

<p><strong>Example 5:</strong></p>

<pre><strong>Input:</strong> arr = [1,2,3,4,5,6,7,8,9,10]
<strong>Output:</strong> 5
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 10^5</code></li>
	<li><code>arr.length</code> is even.</li>
	<li><code>1 &lt;= arr[i] &lt;= 10^5</code></li>
</ul></div>

---




```cpp
class Solution {
public:
    int minSetSize(vector<int>& arr) {
        vector<pair<int,int>> v;
        unordered_map<int,int> m;
        int n=arr.size();
        for(auto i: arr)
            m[i]++;
        int total=0;
        for(auto i:m){
            v.push_back({i.second,i.first});
            total+=i.second;
        }
        sort(v.begin(),v.end());
        reverse(v.begin(),v.end());
        int k=0;
        while(total>n/2){
            total-=v[k].first;
            k++;
        }
        return k;
    }
};
```
