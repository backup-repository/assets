---
title: 0669 Trim A Binary Search Tree
summary: 0669 Trim A Binary Search Tree LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "0669-trim-a-binary-search-tree LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0669 Trim A Binary Search Tree - Solution Explained/problem-solving.webp
    alt: 0669 Trim A Binary Search Tree
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/trim-a-binary-search-tree/">669. Trim a Binary Search Tree</a></h2><h3>Medium</h3><hr><div><p>Given the <code>root</code> of a binary search tree and the lowest and highest boundaries as <code>low</code> and <code>high</code>, trim the tree so that all its elements lies in <code>[low, high]</code>. Trimming the tree should <strong>not</strong> change the relative structure of the elements that will remain in the tree (i.e., any node's descendant should remain a descendant). It can be proven that there is a <strong>unique answer</strong>.</p>

<p>Return <em>the root of the trimmed binary search tree</em>. Note that the root may change depending on the given bounds.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/09/trim1.jpg" style="width: 450px; height: 126px;">
<pre><strong>Input:</strong> root = [1,0,2], low = 1, high = 2
<strong>Output:</strong> [1,null,2]
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/09/trim2.jpg" style="width: 450px; height: 277px;">
<pre><strong>Input:</strong> root = [3,0,4,null,2,null,null,1], low = 1, high = 3
<strong>Output:</strong> [3,2,null,1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 10<sup>4</sup>]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 10<sup>4</sup></code></li>
	<li>The value of each node in the tree is <strong>unique</strong>.</li>
	<li><code>root</code> is guaranteed to be a valid binary search tree.</li>
	<li><code>0 &lt;= low &lt;= high &lt;= 10<sup>4</sup></code></li>
</ul>
</div>

---




```python
class Solution:
    def trimBST(self, root: Optional[TreeNode], low: int, high: int) -> Optional[TreeNode]:
        def solve(root):
            if not root: return 
            if root.val < low:
                root = solve(root.right)
            elif root.val > high:
                root = solve(root.left)
            else:
                root.left = solve(root.left)
                root.right = solve(root.right)
            return root
        
        return solve(root)
        
        
# Time: O(N)
# Space: O(1)
```
