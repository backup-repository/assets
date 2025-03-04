---
title: 2360 Longest Cycle In A Graph
summary: 2360 Longest Cycle In A Graph LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "2360-longest-cycle-in-a-graph LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2360 Longest Cycle In A Graph - Solution Explained/problem-solving.webp
    alt: 2360 Longest Cycle In A Graph
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/longest-cycle-in-a-graph/">2360. Longest Cycle in a Graph</a></h2><h3>Hard</h3><hr><div><p>You are given a <strong>directed</strong> graph of <code>n</code> nodes numbered from <code>0</code> to <code>n - 1</code>, where each node has <strong>at most one</strong> outgoing edge.</p>

<p>The graph is represented with a given <strong>0-indexed</strong> array <code>edges</code> of size <code>n</code>, indicating that there is a directed edge from node <code>i</code> to node <code>edges[i]</code>. If there is no outgoing edge from node <code>i</code>, then <code>edges[i] == -1</code>.</p>

<p>Return <em>the length of the <strong>longest</strong> cycle in the graph</em>. If no cycle exists, return <code>-1</code>.</p>

<p>A cycle is a path that starts and ends at the <strong>same</strong> node.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2022/06/08/graph4drawio-5.png" style="width: 335px; height: 191px;">
<pre><strong>Input:</strong> edges = [3,3,4,2,3]
<strong>Output:</strong> 3
<strong>Explanation:</strong> The longest cycle in the graph is the cycle: 2 -&gt; 4 -&gt; 3 -&gt; 2.
The length of this cycle is 3, so 3 is returned.
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2022/06/07/graph4drawio-1.png" style="width: 171px; height: 161px;">
<pre><strong>Input:</strong> edges = [2,-1,3,1]
<strong>Output:</strong> -1
<strong>Explanation:</strong> There are no cycles in this graph.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == edges.length</code></li>
	<li><code>2 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>-1 &lt;= edges[i] &lt; n</code></li>
	<li><code>edges[i] != i</code></li>
</ul>
</div>

---




```python
class Solution:
    def longestCycle(self, edges: List[int]) -> int:
        n=len(edges)
        bl=[0]*n
        mp=defaultdict(int)
        mx=-1
        for i in range(n):
            if(bl[i]==0):
                x=i
                l=0
                st=set()
                while x>-1 and bl[x]==0:
                    bl[x]=1
                    mp[x]=l
                    l+=1
                    st.add(x)
                    x=edges[x]
                if(x!=-1 and x in st): mx=max(mx,l-mp[x])
        return mx

```
