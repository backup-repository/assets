---
title: Tower Of Hanoi
summary: Tower Of Hanoi LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "Tower Of Hanoi LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Tower Of Hanoi - Solution Explained/problem-solving.webp
    alt: Tower Of Hanoi
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://practice.geeksforgeeks.org/problems/tower-of-hanoi-1587115621/1">Tower Of Hanoi</a></h2><h3>Difficulty Level : Medium</h3><hr><div class="problems_problem_content__Xm_eO"><p><span style="font-size: 18px;">The <a href="https://en.wikipedia.org/wiki/Tower_of_Hanoi">tower of Hanoi</a></span> <span style="font-size: 18px;">is a famous puzzle where we have three rods and <strong>N</strong> disks. The objective of the puzzle is to move the entire stack to another rod. You are given the number of discs <strong>N</strong>. Initially, these discs are in the rod 1. You need to print all the steps of discs movement so that all the discs reach the 3<sup>rd</sup> rod. Also, you need to find the total moves.<br><strong>Note: </strong>The discs are arranged such that the<strong> top disc is numbered 1 </strong>and the<strong> bottom-most disc is numbered N</strong>. Also, all the discs have <strong>different sizes</strong> and a bigger disc <strong>cannot</strong> be put on the top of a smaller disc. Refer the provided link to get a better clarity about the puzzle.</span></p>
<p><span style="font-size: 18px;"><strong>Example 1:</strong></span></p>
<pre><span style="font-size: 18px;"><strong>Input:
</strong>N = 2
<strong>Output:
</strong>move disk 1 from rod 1 to rod 2
move disk 2 from rod 1 to rod 3
move disk 1 from rod 2 to rod 3
3<strong>
Explanation: </strong>For N=2&nbsp;, steps will be
as follows in the example and total
3 steps will be taken.</span></pre>
<p><span style="font-size: 18px;"><strong>Example 2:</strong></span></p>
<pre><span style="font-size: 18px;"><strong>Input:
</strong>N = 3
<strong>Output:
</strong>move disk 1 from rod 1 to rod 3
move disk 2 from rod 1 to rod 2
move disk 1 from rod 3 to rod 2
move disk 3 from rod 1 to rod 3
move disk 1 from rod 2 to rod 1
move disk 2 from rod 2 to rod 3
move disk 1 from rod 1 to rod 3
7<strong>
Explanation: </strong>For N=3 , steps will be
as follows in the example and total
7 steps will be taken.</span>
</pre>
<p><strong><span style="font-size: 18px;">Your Task:</span></strong><br><span style="font-size: 18px;">You don't need to read input . You only need to complete the function <strong>toh()</strong> that takes following parameters: <strong>N</strong> (number of discs),&nbsp;<strong>from</strong> (The rod number from which we move the disc), <strong>to</strong> (The rod number to which we move the disc),&nbsp;<strong>aux</strong> (The rod that is used as an auxiliary rod)&nbsp;and prints the required moves inside function body (See the example for the format of the output) as well as return the count of total moves made.&nbsp;The total number of moves are printed by the driver code.<br><strong>Please take care of the case of the letters.</strong></span></p>
<p><span style="font-size: 18px;"><strong>Expected Time Complexity:&nbsp;</strong>O(2<sup>N</sup>).<br><strong>Expected Auxiliary Space:&nbsp;</strong>O(N).</span></p>
<p><strong><span style="font-size: 18px;">Constraints:</span></strong><br><span style="font-size: 18px;">0 &lt;= N &lt;= 16</span></p></div><p><span style=font-size:18px><strong>Company Tags : </strong><br><code>Flipkart</code>&nbsp;<code>Microsoft</code>&nbsp;<br><p><span style=font-size:18px><strong>Topic Tags : </strong><br><code>Recursion</code>&nbsp;<code>Algorithms</code>&nbsp;

---




```python
# User function Template for python3

class Solution:
    def toh(self, n, from_rod, to_rod, aux_rod):
        if n == 0: 
            return 0
        moves = 1
        moves += self.toh(n-1, from_rod, aux_rod, to_rod)
        print("move disk", n, "from rod", from_rod, "to rod", to_rod)
        moves += self.toh(n-1, aux_rod, to_rod, from_rod)
        return moves
        
        


#{ 
 # Driver Code Starts
# Initial Template for Python 3


import math


def main():

    T = int(input())

    while(T > 0):
        N = int(input())
        ob = Solution()
        print(ob.toh(N, 1, 3, 2))
        T -= 1
if __name__ == "__main__":
    main()


# } Driver Code Ends
```
