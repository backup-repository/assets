---
title: Binary Search Tree To Greater Sum Tree
summary: Binary Search Tree To Greater Sum Tree LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "binary-search-tree-to-greater-sum-tree LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Binary Search Tree To Greater Sum Tree - Solution Explained/problem-solving.webp
    alt: Binary Search Tree To Greater Sum Tree
    hiddenInList: true
    hiddenInSingle: false
---


<h2>1038. Binary Search Tree to Greater Sum Tree</h2><h3>Medium</h3><hr><div><p>Given the <code>root</code> of a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus sum of all keys greater than the original key in BST.</p>

<p>As a reminder, a <em>binary search tree</em> is a tree that satisfies these constraints:</p>

<ul>
	<li>The left subtree of a node contains only nodes with keys&nbsp;<strong>less than</strong>&nbsp;the node's key.</li>
	<li>The right subtree of a node contains only nodes with keys&nbsp;<strong>greater than</strong>&nbsp;the node's key.</li>
	<li>Both the left and right subtrees must also be binary search trees.</li>
</ul>

<p><strong>Note:</strong> This question is the same as 538:&nbsp;<a href="https://leetcode.com/problems/convert-bst-to-greater-tree/">https://leetcode.com/problems/convert-bst-to-greater-tree/</a></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/05/02/tree.png" style="width: 550px; height: 375px;">
<pre><strong>Input:</strong> root = [4,1,6,0,2,5,7,null,null,null,3,null,null,null,8]
<strong>Output:</strong> [30,36,21,36,35,26,15,null,null,null,33,null,null,null,8]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> root = [0,null,1]
<strong>Output:</strong> [1,null,1]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> root = [1,0,2]
<strong>Output:</strong> [3,3,2]
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> root = [3,2,4,1]
<strong>Output:</strong> [7,9,4,10]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 100]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 100</code></li>
	<li>All the values in the tree are <strong>unique</strong>.</li>
	<li><code>root</code> is guaranteed to be a valid binary search tree.</li>
</ul></div>

---




```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    TreeNode* bstToGst(TreeNode* root) {
        int sum=0;
        stack<TreeNode*> s;
        TreeNode* temp=root;
        while(!s.empty() || temp!=NULL){
            while(temp!=NULL){
                s.push(temp);
                temp=temp->right;
            }
            temp=s.top();
            s.pop();
            sum+=temp->val;
            temp->val=sum;
            temp=temp->left;
        }
        return root;
    }
};
```
