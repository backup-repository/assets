---
title: 237 Delete Node In A Linked List
summary: 237 Delete Node In A Linked List LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "237-delete-node-in-a-linked-list LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:237 Delete Node In A Linked List - Solution Explained/problem-solving.webp
    alt: 237 Delete Node In A Linked List
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/delete-node-in-a-linked-list/">237. Delete Node in a Linked List</a></h2><h3>Easy</h3><hr><div><p>Write a function to <strong>delete a node</strong> in a singly-linked list. You will <strong>not</strong> be given access to the <code>head</code> of the list, instead you will be given access to <strong>the node to be deleted</strong> directly.</p>

<p>It is <strong>guaranteed</strong> that the node to be deleted is <strong>not a tail node</strong> in the list.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/01/node1.jpg" style="width: 300px; height: 215px;">
<pre><strong>Input:</strong> head = [4,5,1,9], node = 5
<strong>Output:</strong> [4,1,9]
<strong>Explanation: </strong>You are given the second node with value 5, the linked list should become 4 -&gt; 1 -&gt; 9 after calling your function.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/01/node2.jpg" style="width: 300px; height: 236px;">
<pre><strong>Input:</strong> head = [4,5,1,9], node = 1
<strong>Output:</strong> [4,5,9]
<strong>Explanation: </strong>You are given the third node with value 1, the linked list should become 4 -&gt; 5 -&gt; 9 after calling your function.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of the nodes in the given list is in the range <code>[2, 1000]</code>.</li>
	<li><code>-1000 &lt;= Node.val &lt;= 1000</code></li>
	<li>The value of each node in the list is <strong>unique</strong>.</li>
	<li>The <code>node</code> to be deleted is <strong>in the list</strong> and is <strong>not a tail</strong> node</li>
</ul>
</div>

---




```python
'''
We are given only the node. the head is not given.
So instead of deleting the given node delete the next node of change the value of
the given node with the next node's value. 
But this approach only change the value of the given node not link with previous node.
'''

class Solution:
    def deleteNode(self, node):
        """
        :type node: ListNode
        :rtype: void Do not return anything, modify node in-place instead.
        """
        node.val = node.next.val
        node.next = node.next.next
        
```
