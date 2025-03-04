---
title: 148 Sort List
summary: 148 Sort List LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "148-sort-list LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:148 Sort List - Solution Explained/problem-solving.webp
    alt: 148 Sort List
    hiddenInList: true
    hiddenInSingle: false
---




---




```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def sortList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head or not head.next: return head
        mid = self.getMid(head)
        left = head
        right = mid.next
        mid.next = None
        return self.mergeList(self.sortList(left), self.sortList(right))
        
    def getMid(self, head):
        if not head: return
        slow = head
        fast = head.next
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
        
        return slow
    
    def mergeList(self, l1, l2):
        if not l1 or not l2: return l2 or l1
        if l1.val <= l2.val:
            a = l1; b = l2
        else:
            a = l2; b = l1
        head = a
        while a:
            if not a.next:
                a.next = b
                return head
            if not b:
                return head
            elif a.next.val > b.val:
                tmp = a.next
                a.next = b
                b = tmp
            a = a.next
        return head
            
            
        
```
