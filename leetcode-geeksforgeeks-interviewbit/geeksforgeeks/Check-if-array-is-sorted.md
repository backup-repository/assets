---
title: Check If Array Is Sorted
summary: Check If Array Is Sorted - GeeksforGeeks Solution Explained
date: 2020-06-20
tags: [geeksforgeeks]
series: [GeeksforGeeks]
keywords: ["GeeksforGeeks", "GeeksforGeeks solution in Python3 C++ Java", "Check If Array Is Sorted Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Check If Array Is Sorted - Solution Explained/problem-solving.webp
    alt: Check If Array Is Sorted
    hiddenInList: true
    hiddenInSingle: false
---


# Check if array is sorted
## Easy
<div class="problems_problem_content__Xm_eO"><p><span style="font-size:18px">Given an array <strong>arr[]&nbsp;</strong>of size <strong>N</strong>, check if it is sorted in non-decreasing order or not.&nbsp;</span></p>

<p><span style="font-size:18px"><strong>Example 1:</strong></span></p>

<pre><span style="font-size:18px"><strong>Input:
</strong>N = 5
arr[] = {10, 20, 30, 40, 50}
<strong>Output:</strong> 1
<strong>Explanation:</strong> The given array is sorted.
</span></pre>

<p><span style="font-size:18px"><strong>Example 2:</strong></span></p>

<pre><span style="font-size:18px"><strong>Input:
</strong>N = 6
arr[] = {90, 80, 100, 70, 40, 30}
<strong>Output:</strong> 0
<strong>Explanation:</strong>&nbsp;The given array is not sorted.</span></pre>

<p><br>
<span style="font-size:18px"><strong>Your Task:</strong><br>
You don't need to read input or print anything. Your task is to complete the function&nbsp;<strong>arraySortedOrNot()</strong>&nbsp;which takes the&nbsp;<strong>arr[]&nbsp;</strong>and N<strong>&nbsp;</strong>as input parameters and returns a <strong>boolean</strong> value (true if it is sorted otherwise false).</span></p>

<p><br>
<span style="font-size:18px"><strong>Expected Time Complexity:</strong>&nbsp;O(N)<br>
<strong>Expected Auxiliary Space:</strong>&nbsp;O(1)</span></p>

<p><br>
<span style="font-size:18px"><strong>Constraints:</strong><br>
1 ≤ N ≤ 10<sup>5</sup><br>
1 ≤ Arr[i] ≤ 10<sup>6</sup></span></p>

<p>&nbsp;</p>
</div>

---




```cpp
//{ Driver Code Starts
// Initial template for C++

#include <bits/stdc++.h>
using namespace std;

// } Driver Code Ends
// User function template for C++

class Solution {
  public:
    bool arraySortedOrNot(int arr[], int n) {
        // code here
        //T.C. => O(N^2)
        // for(int i = 0; i < n; i++) {
        //     for(int j = i + 1; j < n; j++){
        //         if(arr[j] < arr[i])
        //         return false;
        //     }
        // }
        // return true;
        
        //T.C. => O(N)
        for(int i = 1; i < n; i++) {
                if(arr[i] < arr[i-1])
                return false;
        }
        return true;
    }
};

//{ Driver Code Starts.

int main() {
    int t;
    cin >> t;
    while (t--) {
        int n;
        cin >> n;
        int arr[n];
        for (int i = 0; i < n; i++) {
            cin >> arr[i];
        }
        Solution ob;
        bool ans = ob.arraySortedOrNot(arr, n);
        cout << ans << "\n";
    }
    return 0;
}

// } Driver Code Ends
```
