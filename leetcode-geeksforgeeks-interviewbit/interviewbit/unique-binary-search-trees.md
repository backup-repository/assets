---
title: Unique Binary Search Trees
summary: Unique Binary Search Trees - Interviewbit Solution Explained
date: 2020-06-20
tags: [interviewbit]
series: [interviewbit]
keywords: ["interviewbit", "interviewbit solution in Python3 C++ Java", "Unique Binary Search Trees Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Unique Binary Search Trees - Solution Explained/problem-solving.webp
    alt: Unique Binary Search Trees
    hiddenInList: true
    hiddenInSingle: false
---

# Unique Binary Search Trees

https://www.interviewbit.com/problems/unique-binary-search-trees/

Given A, generate all structurally unique BST's (binary search trees) that store values 1...A.

### Example

Given A = 3, your program should return all 5 unique BST's shown below.

```
   1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3
```


## Solution
```cpp
vector<TreeNode *> generate(int start, int end) {
    vector<TreeNode *> v;

    if (start > end) {
        v.push_back(NULL);
        return v;
    }

    if (start == end) {
        v.push_back(new TreeNode(start));
        return v;
    }

    for (auto i = start; i <= end; i++) {
        vector<TreeNode *> lft = generate(start, i - 1);
        vector<TreeNode *> rgt = generate(i + 1, end);

        for (auto l : lft) {
            for (auto r : rgt) {
                TreeNode *root = new TreeNode(i);

                root->left = l;
                root->right = r;

                v.push_back(root);
            }
        }
    }
    return v;
}

vector<TreeNode *> Solution::generateTrees(int n) {

    if (n == 0)
        return vector<TreeNode *>();
    else
        return generate(1, n);
}
```

## Asked in
* Amazon
* Twitter


