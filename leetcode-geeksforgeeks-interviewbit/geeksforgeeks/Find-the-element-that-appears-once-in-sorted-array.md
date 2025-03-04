---
title: Find The Element That Appears Once In Sorted Array
summary: Find The Element That Appears Once In Sorted Array - GeeksforGeeks Solution Explained
date: 2020-06-20
tags: [geeksforgeeks]
series: [GeeksforGeeks]
keywords: ["GeeksforGeeks", "GeeksforGeeks solution in Python3 C++ Java", "Find The Element That Appears Once In Sorted Array Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Find The Element That Appears Once In Sorted Array - Solution Explained/problem-solving.webp
    alt: Find The Element That Appears Once In Sorted Array
    hiddenInList: true
    hiddenInSingle: false
---


# Find the element that appears once in sorted array
## Easy
<div class="problems_problem_content__Xm_eO"><p><span style="font-size:18px">Given a sorted array arr[] of size N. Find the element that appears only once in the array. All other elements appear exactly twice.&nbsp;</span></p>

<p><strong><span style="font-size:18px">Example 1:</span></strong></p>

<pre><span style="font-size:18px"><strong>Input:</strong>
N = 11
arr[] = {1, 1, 2, 2, 3, 3, 4, 50, 50, 65, 65}
<strong>Output:</strong> 4
<strong>Explanation:</strong> 4 is the only element that 
appears exactly once.</span></pre>

<p>&nbsp;</p>

<p><span style="font-size:18px"><strong>Your Task: &nbsp;</strong><br>
You don't need to read input or print anything. Complete the function<strong> findOnce() </strong>which takes sorted array and its size as its input parameter and returns the element that appears only once.&nbsp;</span></p>

<p><br>
<span style="font-size:18px"><strong>Expected Time Complexity:</strong> O(log N)<br>
<strong>Expected Auxiliary Space:</strong> O(1)</span></p>

<p>&nbsp;</p>

<p><span style="font-size:18px"><strong>Constraints:</strong><br>
1&nbsp;&lt;= N &lt;= 10<sup>5</sup><br>
-10<sup>5</sup>&nbsp;&lt;= arr[i] &lt;=&nbsp;10<sup>5</sup></span></p>

<p>&nbsp;</p>
</div>

---




```cpp
//{ Driver Code Starts
// Driver code

#include<bits/stdc++.h>
using namespace std;


// } Driver Code Ends
class Solution
{
  public:
    int findOnce(int arr[], int n)
    {
        //code here.
        int res = 0;
        for(int i = 0; i < n; i++){
            res ^= arr[i];
        }
        return res;
    }
};

//{ Driver Code Starts.

int main()
{
    int t;
    cin >> t;

    while (t--)
    {
        int n;
        cin >> n;
        int A[n];
        for(int i = 0;i < n;i++)
        {
            cin>>A[i];
        }
        
        Solution ob;
        
        int res = ob.findOnce(A,n);
        cout << res << endl;
    }
    
    return 0;
}
// } Driver Code Ends
```
