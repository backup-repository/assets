---
title: Insertion Sort List
summary: Insertion Sort List LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "insertion-sort-list LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Insertion Sort List - Solution Explained/problem-solving.webp
    alt: Insertion Sort List
    hiddenInList: true
    hiddenInSingle: false
---


<h2>147. Insertion Sort List</h2><h3>Medium</h3><hr><div><p>Sort a linked list using insertion sort.</p>

<ol>
</ol>

<p><img alt="" src="https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif" style="height:180px; width:300px"><br>
<small>A graphical example of insertion sort. The partial sorted list (black) initially contains only the first element in the list.<br>
With each iteration one element (red) is removed from the input data and inserted in-place into the sorted list</small><br>
&nbsp;</p>

<ol>
</ol>

<p><strong>Algorithm of Insertion Sort:</strong></p>

<ol>
	<li>Insertion sort iterates, consuming one input element each repetition, and growing a sorted output list.</li>
	<li>At each iteration, insertion sort removes one element from the input data, finds the location it belongs within the sorted list, and inserts it there.</li>
	<li>It repeats until no input elements remain.</li>
</ol>

<p><br>
<strong>Example 1:</strong></p>

<pre><strong>Input:</strong> 4-&gt;2-&gt;1-&gt;3
<strong>Output:</strong> 1-&gt;2-&gt;3-&gt;4
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> -1-&gt;5-&gt;3-&gt;4-&gt;0
<strong>Output:</strong> -1-&gt;0-&gt;3-&gt;4-&gt;5
</pre>
</div>

---




```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* insertionSortList(ListNode* head) {
        ListNode* dummy = new ListNode(0);
        dummy -> next = head;
        ListNode *pre = dummy, *cur = head;
        while (cur) {
            if ((cur -> next) && (cur -> next -> val < cur -> val)) {
                while ((pre -> next) && (pre -> next -> val < cur -> next -> val)) {
                    pre = pre -> next;
                }
                ListNode* temp = pre -> next;
                pre -> next = cur -> next;
                cur -> next = cur -> next -> next;
                pre -> next -> next = temp;
                pre = dummy;
            }
            else {
                cur = cur -> next;
            }
        }
        return dummy -> next;
    }
};
```
