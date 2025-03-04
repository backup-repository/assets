---
title: Merge K Sorted Lists
summary: Merge K Sorted Lists LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "merge-k-sorted-lists LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Merge K Sorted Lists - Solution Explained/problem-solving.webp
    alt: Merge K Sorted Lists
    hiddenInList: true
    hiddenInSingle: false
---


<h2>23. Merge k Sorted Lists</h2><h3>Hard</h3><hr><div><p>You are given an array of <code>k</code> linked-lists <code>lists</code>, each linked-list is sorted in ascending order.</p>

<p><em>Merge all the linked-lists into one sorted linked-list and return it.</em></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> lists = [[1,4,5],[1,3,4],[2,6]]
<strong>Output:</strong> [1,1,2,3,4,4,5,6]
<strong>Explanation:</strong> The linked-lists are:
[
  1-&gt;4-&gt;5,
  1-&gt;3-&gt;4,
  2-&gt;6
]
merging them into one sorted list:
1-&gt;1-&gt;2-&gt;3-&gt;4-&gt;4-&gt;5-&gt;6
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> lists = []
<strong>Output:</strong> []
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> lists = [[]]
<strong>Output:</strong> []
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>k == lists.length</code></li>
	<li><code>0 &lt;= k &lt;= 10^4</code></li>
	<li><code>0 &lt;= lists[i].length &lt;= 500</code></li>
	<li><code>-10^4 &lt;= lists[i][j] &lt;= 10^4</code></li>
	<li><code>lists[i]</code> is sorted in <strong>ascending order</strong>.</li>
	<li>The sum of <code>lists[i].length</code> won't exceed <code>10^4</code>.</li>
</ul>
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
    
    struct comp{
        bool operator()(ListNode* a, ListNode* b){
        return a->val>b->val;
        }
    };
    
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        int n=lists.size();
        if(n==0)
            return NULL;
        if(n==1)
            return lists[0];
        priority_queue<ListNode*, vector<ListNode*>, comp> pq;
        for(int i=0;i<n;i++){
            ListNode* head=lists[i];
            while(head!=NULL){
                ListNode* t=head->next;
                head->next=NULL;
                pq.push(head);
                head=t;
            }
        }
        ListNode* dummy = new ListNode(0);
        ListNode* temp=dummy;
        while(!pq.empty()){
            temp->next=pq.top();
            pq.pop();
            temp=temp->next;
        }
        return dummy->next;
    }
};
```
