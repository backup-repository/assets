---
title: 889 Construct Binary Tree From Preorder And Postorder Traversal
summary: 889 Construct Binary Tree From Preorder And Postorder Traversal LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "889-construct-binary-tree-from-preorder-and-postorder-traversal LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:889 Construct Binary Tree From Preorder And Postorder Traversal - Solution Explained/problem-solving.webp
    alt: 889 Construct Binary Tree From Preorder And Postorder Traversal
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/construct-binary-tree-from-preorder-and-postorder-traversal/">889. Construct Binary Tree from Preorder and Postorder Traversal</a></h2><h3>Medium</h3><hr><div><p>Given two integer arrays, <code>preorder</code> and <code>postorder</code> where <code>preorder</code> is the preorder traversal of a binary tree of <strong>distinct</strong> values and <code>postorder</code> is the postorder traversal of the same tree, reconstruct and return <em>the binary tree</em>.</p>

<p>If there exist multiple answers, you can <strong>return any</strong> of them.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/07/24/lc-prepost.jpg" style="width: 304px; height: 265px;">
<pre><strong>Input:</strong> preorder = [1,2,4,5,3,6,7], postorder = [4,5,2,6,7,3,1]
<strong>Output:</strong> [1,2,3,4,5,6,7]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> preorder = [1], postorder = [1]
<strong>Output:</strong> [1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= preorder.length &lt;= 30</code></li>
	<li><code>1 &lt;= preorder[i] &lt;= preorder.length</code></li>
	<li>All the values of <code>preorder</code> are <strong>unique</strong>.</li>
	<li><code>postorder.length == preorder.length</code></li>
	<li><code>1 &lt;= postorder[i] &lt;= postorder.length</code></li>
	<li>All the values of <code>postorder</code> are <strong>unique</strong>.</li>
	<li>It is guaranteed that <code>preorder</code> and <code>postorder</code> are the preorder traversal and postorder traversal of the same binary tree.</li>
</ul>
</div>

---




```python
class Solution:
    def constructFromPrePost(self, preorder, postorder):
        
        def dfs(preorder, postorder):
            if postorder:
                if len(postorder) == 1:
                    return TreeNode(preorder.pop(0))
                root = TreeNode(preorder.pop(0))
                i = postorder.index(preorder[0])
                root.left = dfs(preorder, postorder[:i+1])
                root.right = dfs(preorder, postorder[i+1:-1])
                return root
        
        return dfs(preorder, postorder)
    
```
