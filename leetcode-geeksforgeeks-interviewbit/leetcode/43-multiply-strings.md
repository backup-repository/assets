---
title: 43 Multiply Strings
summary: 43 Multiply Strings LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "43-multiply-strings LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:43 Multiply Strings - Solution Explained/problem-solving.webp
    alt: 43 Multiply Strings
    hiddenInList: true
    hiddenInSingle: false
---




---




```python
class Solution:
    def multiply(self, num1: str, num2: str) -> str:
        if num1 == '0' or num2 == '0': return '0'
        
        arr = [0] * (len(num1) + len(num2))
        
        for i in range(len(num1)-1, -1, -1):
            for j in range(len(num2)-1, -1, -1):
                n1 = ord(num1[i]) - ord('0')
                n2 = ord(num2[j]) - ord('0')
                arr[i+j+1] += n1 * n2
                arr[i+j] += arr[i+j+1] // 10
                arr[i+j+1] %= 10
        
        res = ""
        flag = False
        for i in range(len(arr)):
            if arr[i] == 0 and flag == False:
                if arr[i+1] == 0:
                    continue
                else:
                    flag = True
            else:
                res += str(arr[i])
                flag = True
                
        return res
```
