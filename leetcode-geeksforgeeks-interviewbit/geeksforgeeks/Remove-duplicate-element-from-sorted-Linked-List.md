---
title: Remove Duplicate Element From Sorted Linked List
summary: Remove Duplicate Element From Sorted Linked List - GeeksforGeeks Solution Explained
date: 2020-06-20
tags: [geeksforgeeks]
series: [GeeksforGeeks]
keywords: ["GeeksforGeeks", "GeeksforGeeks solution in Python3 C++ Java", "Remove Duplicate Element From Sorted Linked List Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Remove Duplicate Element From Sorted Linked List - Solution Explained/problem-solving.webp
    alt: Remove Duplicate Element From Sorted Linked List
    hiddenInList: true
    hiddenInSingle: false
---


# Remove duplicate element from sorted Linked List
## Easy
<div class="problems_problem_content__Xm_eO"><p><span style="font-size:18px">Given a singly linked list consisting of <strong>N</strong> nodes. The task is to remove duplicates (nodes with duplicate values) from the given list (if exists).</span><br>
<span style="font-size:18px"><strong>Note:</strong> Try not to use extra space. Expected time complexity is <strong>O(N)</strong>. The nodes are arranged in a <strong>sorted </strong>way.</span></p>

<p><span style="font-size:18px"><strong>Example 1:</strong></span></p>

<pre><span style="font-size:18px"><strong>Input:
</strong>LinkedList: 2-&gt;2-&gt;4-&gt;5
<strong>Output: </strong>2 4 5<strong>
Explanation: </strong>In the given linked list 
2 -&gt;2 -&gt; 4-&gt; 5, only 2 occurs more 
than 1 time.</span>
</pre>

<p><span style="font-size:18px"><strong>Example 2:</strong></span></p>

<pre><span style="font-size:18px"><strong>Input:
</strong>LinkedList: 2-&gt;2-&gt;2-&gt;2-&gt;2
<strong>Output: </strong>2<strong>
Explanation: </strong>In the given linked list 
2 -&gt;2 -&gt;2 -&gt;2 -&gt;2, 2 is the only element
and is repeated 5 times.</span></pre>

<p><span style="font-size:18px"><strong>Your Task:</strong><br>
The task is to complete the function&nbsp;<strong>removeDuplicates</strong>() which should remove the duplicates from linked list and return the head of the linkedlist.</span></p>

<p><span style="font-size:18px"><strong>Expected Time Complexity</strong> : O(N)<br>
<strong>Expected Auxilliary Space</strong> : O(1)</span></p>

<p><span style="font-size:18px"><strong>Constraints:</strong><br>
1 &lt;= Number of nodes &lt;= 10<sup>4</sup></span></p>

<p>&nbsp;</p>
</div>

---




```cpp
//{ Driver Code Starts
#include <bits/stdc++.h>
using namespace std;

struct Node {
  int data;
  struct Node *next;
  Node(int x) {
    data = x;
    next = NULL;
  }
};


void print(Node *root)
{
    Node *temp = root;
    while(temp!=NULL)
    {
    cout<<temp->data<<" ";
    temp=temp->next;
    }
}
Node* removeDuplicates(Node *root);
int main() {
	// your code goes here
	int T;
	cin>>T;

	while(T--)
	{
		int K;
		cin>>K;
		Node *head = NULL;
        Node *temp = head;

		for(int i=0;i<K;i++){
		int data;
		cin>>data;
			if(head==NULL)
			head=temp=new Node(data);
			else
			{
				temp->next = new Node(data);
				temp=temp->next;
			}
		}
		
		Node *result  = removeDuplicates(head);
		print(result);
		cout<<endl;
	}
	return 0;
}
// } Driver Code Ends


/*
struct Node {
  int data;
  struct Node *next;
  Node(int x) {
    data = x;
    next = NULL;
  }
};*/

//Function to remove duplicates from sorted linked list.
Node *removeDuplicates(Node *head)
{
 // your code goes here
 Node* current = head;
 while(current != NULL && current->next != NULL) {
     if(current->data == current->next->data) {
         current->next = current->next->next;
     }
     else {
         current = current->next;
     }
 }
 return head;
}
```
