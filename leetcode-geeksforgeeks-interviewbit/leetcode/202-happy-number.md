---
title: 202 Happy Number
summary: 202 Happy Number LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "202-happy-number LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:202 Happy Number - Solution Explained/problem-solving.webp
    alt: 202 Happy Number
    hiddenInList: true
    hiddenInSingle: false
---




---




```python
class Solution:
    def isHappy(self, n: int) -> bool:
        visited = set()        
        while n != 1:
            a = str(n)
            n = 0
            for i in a:
                n += int(i)**2
            if n == 1: return True
            if n in visited: return False
            visited.add(n)
            
        return True
```
