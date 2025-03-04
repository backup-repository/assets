---
title: C++ Data Types
summary: C++ Data Types - GeeksforGeeks Solution Explained
date: 2020-06-20
tags: [geeksforgeeks]
series: [GeeksforGeeks]
keywords: ["GeeksforGeeks", "GeeksforGeeks solution in Python3 C++ Java", "C++ Data Types Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:C++ Data Types - Solution Explained/problem-solving.webp
    alt: C++ Data Types
    hiddenInList: true
    hiddenInSingle: false
---


# C++ Data Types
## Easy
<div class="problems_problem_content__Xm_eO"><p><span style="font-size:18px">Read a value and store it in the appropriate C++ Data Type.&nbsp;</span></p>

<p><span style="font-size:18px"><strong>Example 1:</strong></span></p>

<pre><span style="font-size:18px"><strong>Input: </strong>
2 h 2.555
<strong>Output:</strong>
2
h
2.555 </span>
<span style="font-size:18px"><strong>Explanation:</strong></span>
<span style="font-size:18px">The three inputs are printed in order.</span>
</pre>

<p>&nbsp;</p>

<p><span style="font-size:18px"><strong>Your Task:</strong><br>
Your task is to complete each of the given functions&nbsp;<br>
<strong>cppIntType() </strong>: read an integer input, store it in appropriate data type and return it.&nbsp;<br>
<strong>cppCharType() :&nbsp;</strong>read a character&nbsp;input, store it in appropriate data type and return it.&nbsp;<strong>&nbsp;<br>
cppFloatType() :&nbsp;</strong>read a float&nbsp;input, store it in appropriate data type and return it.&nbsp;</span></p>

<p><br>
<span style="font-size:18px"><strong>Expected Time Complexity:</strong> O(1)<br>
<strong>Expected Auxiliary Space:</strong> O(1)</span></p>

<p>&nbsp;</p>
</div>

---




```cpp
//{ Driver Code Starts
#include <bits/stdc++.h>
using namespace std;

// } Driver Code Ends
class Solution {
  public:
    int cppIntType() {
        // code here
        int a;
        cin>>a;
        return a;
    }
    
    char cppCharType() {
        // code here
        char b;
        cin>>b;
        return b;
    }
    
    float cppFloatType() {
        // code here
        float c;
        cin>>c;
        return c;
    }
};

//{ Driver Code Starts.
int main() {
    int t;
    cin >> t;
    while (t--) {
        Solution ob;
        cout << ob.cppIntType() << endl;
        cout << ob.cppCharType() << endl;
        cout << ob.cppFloatType() << endl;
    }
    return 0;
}
// } Driver Code Ends
```
