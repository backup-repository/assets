---
title: 61 Rotate List
summary: 61 Rotate List LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "61-rotate-list LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:61 Rotate List - Solution Explained/problem-solving.webp
    alt: 61 Rotate List
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/rotate-list/">61. Rotate List</a></h2><h3>Medium</h3><hr><div><p>Given the <code>head</code> of a linked&nbsp;list, rotate the list to the right by <code>k</code> places.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/13/rotate1.jpg" style="width: 450px; height: 191px;">
<pre><strong>Input:</strong> head = [1,2,3,4,5], k = 2
<strong>Output:</strong> [4,5,1,2,3]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/13/roate2.jpg" style="width: 305px; height: 350px;">
<pre><strong>Input:</strong> head = [0,1,2], k = 4
<strong>Output:</strong> [2,0,1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the list is in the range <code>[0, 500]</code>.</li>
	<li><code>-100 &lt;= Node.val &lt;= 100</code></li>
	<li><code>0 &lt;= k &lt;= 2 * 10<sup>9</sup></code></li>
</ul>
</div>

---




```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def rotateRight(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:        
        if not head or not head.next: return head
        
        dummy = ListNode(-1)
        dummy.next = head
        fast = dummy
        slow = dummy
        a = head
        
        length = 0
        while a:
            length += 1
            a = a.next
        
        k = k % length
        
        if k == 0: return head
        
        while k > 0 and fast:
            fast = fast.next
            k -= 1
        
        while fast.next:
            fast = fast.next
            slow = slow.next
        
        tmp = slow.next
        slow.next = None
        
        fast.next = dummy.next
        dummy.next = tmp
        
        return dummy.next
```
