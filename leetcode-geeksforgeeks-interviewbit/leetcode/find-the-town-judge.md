---
title: Find The Town Judge
summary: Find The Town Judge LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "find-the-town-judge LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Find The Town Judge - Solution Explained/problem-solving.webp
    alt: Find The Town Judge
    hiddenInList: true
    hiddenInSingle: false
---


<h2>997. Find the Town Judge</h2><h3>Easy</h3><hr><div><p>In a town, there are <code>N</code> people labelled from&nbsp;<code>1</code> to <code>N</code>.&nbsp; There is a rumor that one of these people is secretly the town judge.</p>

<p>If the&nbsp;town judge exists, then:</p>

<ol>
	<li>The town judge trusts nobody.</li>
	<li>Everybody (except for the town judge) trusts the town judge.</li>
	<li>There is exactly one person that satisfies properties 1 and 2.</li>
</ol>

<p>You are given <code>trust</code>, an array of pairs <code>trust[i] = [a, b]</code> representing that the person labelled <code>a</code> trusts the person labelled <code>b</code>.</p>

<p>If the town judge exists and can be identified, return the label of the town judge.&nbsp; Otherwise, return <code>-1</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> N = 2, trust = [[1,2]]
<strong>Output:</strong> 2
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> N = 3, trust = [[1,3],[2,3]]
<strong>Output:</strong> 3
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> N = 3, trust = [[1,3],[2,3],[3,1]]
<strong>Output:</strong> -1
</pre><p><strong>Example 4:</strong></p>
<pre><strong>Input:</strong> N = 3, trust = [[1,2],[2,3]]
<strong>Output:</strong> -1
</pre><p><strong>Example 5:</strong></p>
<pre><strong>Input:</strong> N = 4, trust = [[1,3],[1,4],[2,3],[2,4],[4,3]]
<strong>Output:</strong> 3
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= N &lt;= 1000</code></li>
	<li><code>0 &lt;= trust.length &lt;= 10^4</code></li>
	<li><code>trust[i].length == 2</code></li>
	<li><code>trust[i]</code> are all different</li>
	<li><code>trust[i][0] != trust[i][1]</code></li>
	<li><code>1 &lt;= trust[i][0], trust[i][1] &lt;= N</code></li>
</ul></div>

---


