---
title: 0085 Maximal Rectangle
summary: 0085 Maximal Rectangle LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "0085-maximal-rectangle LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0085 Maximal Rectangle - Solution Explained/problem-solving.webp
    alt: 0085 Maximal Rectangle
    hiddenInList: true
    hiddenInSingle: false
---




---




```python
# https://leetcode.com/problems/maximal-rectangle/
# https://youtu.be/tOylVCugy9k


class Solution:
    def maximalRectangle(self, matrix: List[List[str]]) -> int:
        if not matrix: return 0
        arr = [0 for i in range(len(matrix[0]))]
        ans = 0
        for i in range(len(matrix)):
            for j in range(len(matrix[0])):
                if matrix[i][j] == "1":
                    arr[j] = arr[j] + 1
                else: arr[j] = 0
            ans = max(ans, self.largestRectangleArea(arr))
        
        return ans
        
    def largestRectangleArea(self, heights):
        stack, lb = [], []
        for i in range(len(heights)):
            while stack:
                if heights[stack[-1]] >= heights[i]: 
                    stack.pop()
                else:
                    lb.append(stack[-1] + 1)
                    stack.append(i)
                    break
            if not stack:
                stack.append(i)
                lb.append(0)
                
        stack, rb = [], []
        for i in range(len(heights) - 1, -1, -1):
            while stack:
                if heights[stack[-1]] >= heights[i]: 
                    stack.pop()
                else:
                    rb.append(stack[-1] - 1)
                    stack.append(i)
                    break
            if not stack:
                stack.append(i)
                rb.append(len(heights) - 1)
        rb = rb[::-1]
        
        res = 0
        for i in range(len(heights)):
            width = abs(lb[i] - rb[i]) + 1
            res = max(res, width * heights[i])
        
        return res
            
            
            
# Time: O(R * C)
# Space: O(C)
```
