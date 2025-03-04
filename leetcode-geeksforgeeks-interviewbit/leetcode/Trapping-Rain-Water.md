---
title: Trapping Rain Water
summary: Trapping Rain Water LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "Trapping Rain Water LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Trapping Rain Water - Solution Explained/problem-solving.webp
    alt: Trapping Rain Water
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://practice.geeksforgeeks.org/problems/trapping-rain-water-1587115621/1?page=1&company[]=Amazon&sortBy=submissions">Trapping Rain Water</a></h2><h3>Difficulty Level : Medium</h3><hr><div class="problems_problem_content__Xm_eO"><p><span style="font-size: 18px;">Given an array <strong>arr[]</strong>&nbsp;of <strong>N</strong> non-negative integers representing the height of blocks. If&nbsp;width of each block is 1, compute how much water can be trapped&nbsp;between the blocks during the rainy season.&nbsp;</span><br>&nbsp;</p>
<p><span style="font-size: 18px;"><strong>Example 1:</strong></span></p>
<pre><span style="font-size: 18px;"><strong>Input:
</strong>N = 6
arr[] = {3,0,0,2,0,4}
<strong>Output:
</strong>10<strong>
Explanation: 
</strong></span><img style="height: 436px; width: 350px;" src="https://media.geeksforgeeks.org/img-practice/PROD/addEditProblem/701211/Web/Other/186b43ba-eeec-4d9e-b0f8-dea91ef026e0_1685086818.png" alt="">
</pre>
<p><span style="font-size: 18px;"><strong>Example 2:</strong></span></p>
<pre><span style="font-size: 18px;"><strong>Input:
</strong>N = 4
arr[] = {7,4,0,9}
<strong>Output:
</strong>10<strong>
Explanation:
</strong>Water trapped by above 
block of height 4 is 3 units and above 
block of height 0 is 7 units. So, the 
total unit of water trapped is 10 units.</span>
</pre>
<p><span style="font-size: 18px;"><strong>Example 3:</strong></span></p>
<pre><span style="font-size: 18px;"><strong>Input:
</strong>N = 3
arr[] = {6,9,9}
<strong>Output:
</strong>0<strong>
Explanation:
</strong>No water will be trapped.</span></pre>
<p><br><span style="font-size: 18px;"><strong>Your Task:</strong><br>You don't&nbsp;need to read input or print anything.&nbsp;The task is to complete the function <strong>trappingWater</strong>() which takes arr[] and N as input parameters and&nbsp;returns the total amount of water that can be trapped.</span></p>
<p><br><span style="font-size: 18px;"><strong>Expected Time Complexity:&nbsp;</strong>O(N)<br><strong>Expected Auxiliary Space:&nbsp;</strong>O(N)</span></p>
<p><br><span style="font-size: 18px;"><strong>Constraints:</strong><br>3 <u>&lt;</u>&nbsp;N <u>&lt;</u>&nbsp;10<sup>6</sup><br>0 <u>&lt;</u>&nbsp;A<sub>i</sub> <u>&lt;</u>&nbsp;10<sup>8</sup></span></p></div><p><span style=font-size:18px><strong>Company Tags : </strong><br><code>Flipkart</code>&nbsp;<code>Amazon</code>&nbsp;<code>Microsoft</code>&nbsp;<code>Google</code>&nbsp;<br><p><span style=font-size:18px><strong>Topic Tags : </strong><br><code>Arrays</code>&nbsp;<code>Dynamic Programming</code>&nbsp;<code>Data Structures</code>&nbsp;<code>Algorithms</code>&nbsp;

---




```python
class Solution:
    #Back-end complete function Template for Python 3
    
    # Function to find the trapped water between the blocks.
    def findWater(self, arr, n): 
      
        # left[i] contains height of tallest bar to the 
        # left of ith bar including itself. 
        left = [0]*n 
      
        # right[i] contains height of tallest bar to 
        # the right of ith bar including itself.
        right = [0]*n 
      
        water = 0
      
        # Storing values of tallest bar from first index till ith index.
        left[0] = arr[0] 
        for i in range( 1, n): 
            left[i] = max(left[i-1], arr[i]) 
      
        # Storing values of tallest bar from last index till ith index.
        right[n-1] = arr[n-1] 
        for i in range(n-2, -1, -1): 
            right[i] = max(right[i+1], arr[i]); 
      
        # Storing the result by choosing the minimum of heights of tallest bar to
        # the right and left of the bar at current index and also subtracting the
        # value of current index to get water accumulated at current index.
        for i in range(0, n): 
            water += min(left[i],right[i]) - arr[i] 
        
        # returning the result.
        return water 
     
    def trappingWater(self, arr,n):
        return self.findWater(arr,n)


#{ 
 # Driver Code Starts
#Initial Template for Python 3

import math



def main():
        T=int(input())
        while(T>0):
            
            n=int(input())
            
            arr=[int(x) for x in input().strip().split()]
            obj = Solution()
            print(obj.trappingWater(arr,n))
            
            
            T-=1


if __name__ == "__main__":
    main()



# } Driver Code Ends
```
