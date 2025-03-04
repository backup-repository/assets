---
title: Minimum Height Trees
summary: Minimum Height Trees LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "minimum-height-trees LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Minimum Height Trees - Solution Explained/problem-solving.webp
    alt: Minimum Height Trees
    hiddenInList: true
    hiddenInSingle: false
---


[Discussion Post (created on 21/1/2021 at 21:31)](https://leetcode.com/problems/minimum-height-trees/discuss/1076511/C%2B%2B-or-O(n))  
<h2>310. Minimum Height Trees</h2><h3>Medium</h3><hr><div><p>A tree is an undirected graph in which any two vertices are connected by&nbsp;<i>exactly</i>&nbsp;one path. In other words, any connected graph without simple cycles is a tree.</p>

<p>Given a tree of <code>n</code> nodes&nbsp;labelled from <code>0</code> to <code>n - 1</code>, and an array of&nbsp;<code>n - 1</code>&nbsp;<code>edges</code> where <code>edges[i] = [a<sub>i</sub>, b<sub>i</sub>]</code> indicates that there is an undirected edge between the two nodes&nbsp;<code>a<sub>i</sub></code> and&nbsp;<code>b<sub>i</sub></code> in the tree,&nbsp;you can choose any node of the tree as the root. When you select a node <code>x</code> as the root, the result tree has height <code>h</code>. Among all possible rooted trees, those with minimum height (i.e. <code>min(h)</code>)&nbsp; are called <strong>minimum height trees</strong> (MHTs).</p>

<p>Return <em>a list of all <strong>MHTs'</strong> root labels</em>.&nbsp;You can return the answer in <strong>any order</strong>.</p>

<p>The <strong>height</strong> of a rooted tree is the number of edges on the longest downward path between the root and a leaf.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/01/e1.jpg" style="width: 800px; height: 213px;">
<pre><strong>Input:</strong> n = 4, edges = [[1,0],[1,2],[1,3]]
<strong>Output:</strong> [1]
<strong>Explanation:</strong> As shown, the height of the tree is 1 when the root is the node with label 1 which is the only MHT.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/01/e2.jpg" style="width: 800px; height: 321px;">
<pre><strong>Input:</strong> n = 6, edges = [[3,0],[3,1],[3,2],[3,4],[5,4]]
<strong>Output:</strong> [3,4]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> n = 1, edges = []
<strong>Output:</strong> [0]
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> n = 2, edges = [[0,1]]
<strong>Output:</strong> [0,1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>edges.length == n - 1</code></li>
	<li><code>0 &lt;= a<sub>i</sub>, b<sub>i</sub> &lt; n</code></li>
	<li><code>a<sub>i</sub> != b<sub>i</sub></code></li>
	<li>All the pairs <code>(a<sub>i</sub>, b<sub>i</sub>)</code> are distinct.</li>
	<li>The given input is <strong>guaranteed</strong> to be a tree and there will be <strong>no repeated</strong> edges.</li>
</ul>
</div>

---




```cpp
class Solution {
public:
    vector<int> findMinHeightTrees(int n, vector<vector<int>>& edges) {
        if(n==1){
            return {0};
        }
        vector<int> adj[n];
        for(vector<int> e: edges){
            adj[e[0]].push_back(e[1]);
            adj[e[1]].push_back(e[0]);
        }
        queue<int> l;
        for(int i=0;i<n;i++){
            if(adj[i].size()==1)
                l.push(i);
        }
        while(n>2){
            int k=l.size();
            n-=k;
            for(int i=0;i<k;i++){
                int curr=l.front();
                l.pop();
                for(auto &p: adj[curr]){
                    auto it=std::find(adj[p].begin(), adj[p].end(), curr);
                    adj[p].erase(it);
                    if(adj[p].size()==1)
                        l.push(p);
                }
            }
        }
        vector<int> ans;
        while(!l.empty()){
            ans.push_back(l.front());
            l.pop();
        }
        return ans;
    }
};
```
