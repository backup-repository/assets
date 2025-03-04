---
title: Course Schedule Ii
summary: Course Schedule Ii LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "course-schedule-ii LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Course Schedule Ii - Solution Explained/problem-solving.webp
    alt: Course Schedule Ii
    hiddenInList: true
    hiddenInSingle: false
---


<h2>210. Course Schedule II</h2><h3>Medium</h3><hr><div><p>There are a total of <code>n</code> courses you have to take labelled from <code>0</code> to <code>n - 1</code>.</p>

<p>Some courses may have <code>prerequisites</code>, for example, if&nbsp;<code>prerequisites[i] = [a<sub>i</sub>, b<sub>i</sub>]</code>&nbsp;this means you must take the course <code>b<sub>i</sub></code> before the course <code>a<sub>i</sub></code>.</p>

<p>Given the total number of courses&nbsp;<code>numCourses</code> and a list of the <code>prerequisite</code> pairs, return the ordering of courses you should take to finish all courses.</p>

<p>If there are many valid answers, return <strong>any</strong> of them.&nbsp;If it is impossible to finish all courses, return <strong>an empty array</strong>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> numCourses = 2, prerequisites = [[1,0]]
<strong>Output:</strong> [0,1]
<strong>Explanation:</strong> There are a total of 2 courses to take. To take course 1 you should have finished course 0. So the correct course order is [0,1].
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> numCourses = 4, prerequisites = [[1,0],[2,0],[3,1],[3,2]]
<strong>Output:</strong> [0,2,1,3]
<strong>Explanation:</strong> There are a total of 4 courses to take. To take course 3 you should have finished both courses 1 and 2. Both courses 1 and 2 should be taken after you finished course 0.
So one correct course order is [0,1,2,3]. Another correct ordering is [0,2,1,3].
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> numCourses = 1, prerequisites = []
<strong>Output:</strong> [0]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= numCourses &lt;= 2000</code></li>
	<li><code>0 &lt;=&nbsp;prerequisites.length &lt;= numCourses * (numCourses - 1)</code></li>
	<li><code>prerequisites[i].length == 2</code></li>
	<li><code>0 &lt;= a<sub>i</sub>, b<sub>i</sub> &lt;&nbsp;numCourses</code></li>
	<li><code>a<sub>i</sub>&nbsp;!=&nbsp;b<sub>i</sub></code></li>
	<li>All the pairs <code>[a<sub>i</sub>, b<sub>i</sub>]</code> are <strong>distinct</strong>.</li>
</ul>
</div>

---




```cpp
class Solution {
public:
    
    bool isCyclic(int v, vector<int> &ans, vector<int> &vis, vector<vector<int>> &adj){
        vis[v]=-1;
        for(int u: adj[v]){
            if(vis[u]==-1)
                return true;
            if(vis[u]==0 && isCyclic(u, ans, vis, adj))
                return true;
        }
        vis[v]=1;
        ans.push_back(v);
        return false;
    }
    
    vector<int> findOrder(int numCourses, vector<vector<int>>& prerequisites) {
        vector<vector<int>> adj(numCourses);
        for(int i=0;i<prerequisites.size();i++)
            adj[prerequisites[i][0]].push_back(prerequisites[i][1]);
        vector<int> vis(numCourses,0);
        vector<int> ans;
        for(int i=0;i<numCourses;i++){
            if(!vis[i]){
                if(isCyclic(i, ans, vis, adj))
                    return {};
            }
        }
        return ans;
    }
};
```
