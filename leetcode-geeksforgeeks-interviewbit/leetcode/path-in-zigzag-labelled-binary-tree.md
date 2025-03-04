---
title: Path In Zigzag Labelled Binary Tree
summary: Path In Zigzag Labelled Binary Tree LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "path-in-zigzag-labelled-binary-tree LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Path In Zigzag Labelled Binary Tree - Solution Explained/problem-solving.webp
    alt: Path In Zigzag Labelled Binary Tree
    hiddenInList: true
    hiddenInSingle: false
---


<h2>1104. Path In Zigzag Labelled Binary Tree</h2><h3>Medium</h3><hr><div><p>In an infinite binary tree where every node has two children, the nodes are labelled in row order.</p>

<p>In the odd numbered rows (ie., the first, third, fifth,...), the labelling is left to right, while in the even numbered rows (second, fourth, sixth,...), the labelling is right to left.</p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2019/06/24/tree.png" style="width: 300px; height: 138px;"></p>

<p>Given the <code>label</code> of a node in this tree, return the labels in the path from the root of the tree to the&nbsp;node with that <code>label</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> label = 14
<strong>Output:</strong> [1,3,4,14]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> label = 26
<strong>Output:</strong> [1,2,6,10,26]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= label &lt;= 10^6</code></li>
</ul>
</div>

---




```cpp
class Solution {
public:
    vector<int> pathInZigZagTree(int label) {
        int l=1,c=1;
        vector<int> ans;
        while(c*2<=label){
            c*=2;
            l++;
        }
        while(label!=0){
            ans.push_back(label);
            int maxi=((int)pow(2,l))-1;
            int mini=((int)pow(2,l-1));
            label=(int)(maxi+mini-label)/2;
            l--;
        }
        reverse(ans.begin(),ans.end());
        return ans;
    }
};
```
