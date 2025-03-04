---
title: Arranging Coins
summary: Arranging Coins LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "arranging-coins LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Arranging Coins - Solution Explained/problem-solving.webp
    alt: Arranging Coins
    hiddenInList: true
    hiddenInSingle: false
---


<h2>441. Arranging Coins</h2><h3>Easy</h3><hr><div><p>You have a total of <i>n</i> coins that you want to form in a staircase shape, where every <i>k</i>-th row must have exactly <i>k</i> coins.</p>
 
<p>Given <i>n</i>, find the total number of <b>full</b> staircase rows that can be formed.</p>

<p><i>n</i> is a non-negative integer and fits within the range of a 32-bit signed integer.</p>

<p><b>Example 1:</b>
</p><pre>n = 5

The coins can form the following rows:
¤
¤ ¤
¤ ¤

Because the 3rd row is incomplete, we return 2.
</pre>
<p></p>

<p><b>Example 2:</b>
</p><pre>n = 8

The coins can form the following rows:
¤
¤ ¤
¤ ¤ ¤
¤ ¤

Because the 4th row is incomplete, we return 3.
</pre>
<p></p></div>

---




```cpp
class Solution {
public:
    
    int arrange(int n, int row){
        if(n<row)
            return row-1;
        return arrange(n-row, row+1);
    }
    
    int arrangeCoins(int n) {
        return arrange(n, 1);
    }
};

```
