---
title: 0530 Minimum Absolute Difference In Bst
summary: 0530 Minimum Absolute Difference In Bst LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "0530 Minimum Absolute Difference In Bst LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0530 Minimum Absolute Difference In Bst - Solution Explained/problem-solving.webp
    alt: 0530 Minimum Absolute Difference In Bst
    hiddenInList: true
    hiddenInSingle: false
---


# [530. Minimum Absolute Difference in BST](https://leetcode.com/problems/minimum-absolute-difference-in-bst)


## Description

<p>Given the <code>root</code> of a Binary Search Tree (BST), return <em>the minimum absolute difference between the values of any two different nodes in the tree</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/solution/0500-0599/0530.Minimum%20Absolute%20Difference%20in%20BST/images/bst1.jpg" style="width: 292px; height: 301px;" />
<pre>
<strong>Input:</strong> root = [4,2,6,1,3]
<strong>Output:</strong> 1
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/solution/0500-0599/0530.Minimum%20Absolute%20Difference%20in%20BST/images/bst2.jpg" style="width: 282px; height: 301px;" />
<pre>
<strong>Input:</strong> root = [1,0,48,null,null,12,49]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[2, 10<sup>4</sup>]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 10<sup>5</sup></code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Note:</strong> This question is the same as 783: <a href="https://leetcode.com/problems/minimum-distance-between-bst-nodes/" target="_blank">https://leetcode.com/problems/minimum-distance-between-bst-nodes/</a></p>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def getMinimumDifference(self, root: TreeNode) -> int:
        def dfs(root):
            if root is None:
                return
            dfs(root.left)
            nonlocal ans, prev
            ans = min(ans, abs(prev - root.val))
            prev = root.val
            dfs(root.right)

        ans = prev = inf
        dfs(root)
        return ans
```

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    private int ans;
    private int prev;
    private int inf = Integer.MAX_VALUE;

    public int getMinimumDifference(TreeNode root) {
        ans = inf;
        prev = inf;
        dfs(root);
        return ans;
    }

    private void dfs(TreeNode root) {
        if (root == null) {
            return;
        }
        dfs(root.left);
        ans = Math.min(ans, Math.abs(root.val - prev));
        prev = root.val;
        dfs(root.right);
    }
}
```

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
    const int inf = INT_MAX;
    int ans;
    int prev;

    int getMinimumDifference(TreeNode* root) {
        ans = inf, prev = inf;
        dfs(root);
        return ans;
    }

    void dfs(TreeNode* root) {
        if (!root) return;
        dfs(root->left);
        ans = min(ans, abs(prev - root->val));
        prev = root->val;
        dfs(root->right);
    }
};
```

```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func getMinimumDifference(root *TreeNode) int {
	inf := 0x3f3f3f3f
	ans, prev := inf, inf
	var dfs func(*TreeNode)
	dfs = func(root *TreeNode) {
		if root == nil {
			return
		}
		dfs(root.Left)
		ans = min(ans, abs(prev-root.Val))
		prev = root.Val
		dfs(root.Right)
	}
	dfs(root)
	return ans
}

func abs(x int) int {
	if x < 0 {
		return -x
	}
	return x
}
```

```rust
// Definition for a binary tree node.
// #[derive(Debug, PartialEq, Eq)]
// pub struct TreeNode {
//   pub val: i32,
//   pub left: Option<Rc<RefCell<TreeNode>>>,
//   pub right: Option<Rc<RefCell<TreeNode>>>,
// }
//
// impl TreeNode {
//   #[inline]
//   pub fn new(val: i32) -> Self {
//     TreeNode {
//       val,
//       left: None,
//       right: None
//     }
//   }
// }
use std::rc::Rc;
use std::cell::RefCell;
impl Solution {
    #[allow(dead_code)]
    pub fn get_minimum_difference(root: Option<Rc<RefCell<TreeNode>>>) -> i32 {
        let mut ret = i32::MAX;
        let mut prev = i32::MAX;
        Self::traverse(root, &mut prev, &mut ret);
        ret
    }

    #[allow(dead_code)]
    fn traverse(root: Option<Rc<RefCell<TreeNode>>>, prev: &mut i32, ans: &mut i32) {
        let left = root.as_ref().unwrap().borrow().left.clone();
        let right = root.as_ref().unwrap().borrow().right.clone();
        let val = root.as_ref().unwrap().borrow().val;
        if !left.is_none() {
            Self::traverse(left.clone(), prev, ans);
        }
        *ans = std::cmp::min(*ans, (*prev - val).abs());
        *prev = val;
        if !right.is_none() {
            Self::traverse(right.clone(), prev, ans);
        }
    }
}
```

<!-- tabs:end -->

<!-- end -->
