---
title: C++ Strings
summary: C++ Strings - GeeksforGeeks Solution Explained
date: 2020-06-20
tags: [geeksforgeeks]
series: [GeeksforGeeks]
aliases: ["/posts/C++-Strings", "/blog/posts/C++-Strings", "/C++-Strings", "/blog/C++-Strings",]
keywords: GeeksforGeeks, GeeksforGeeks solution in Python3 C++ Java, C++ Strings solution
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_70_bold:C++ Strings - Solution Explained/problem-solving.webp
    alt: C++ Strings
    hiddenInList: true
    hiddenInSingle: false
---


# C++ Strings
## Easy
<div class="problems_problem_content__Xm_eO"><p><span style="font-size:18px">Given two strings&nbsp; S1 and S2 .&nbsp;You have to concatenate both the strings and print the concatenated string.</span></p>

<p><span style="font-size:18px"><strong>Example 1:</strong></span></p>

<pre><span style="font-size:18px"><strong>Input:</strong>
S1 = "Geeksfor"
S2 = "Geeks"
<strong>Output:</strong> GeeksforGeeks
<strong>Explanation: </strong>Combined "Geeksfor" and "Geeks"</span></pre>

<p>&nbsp;</p>

<p><span style="font-size:18px"><strong>Example 2:</strong></span></p>

<pre><span style="font-size:18px"><strong>Input:</strong>
S1 = "Practice"
S2 = "Hard"
<strong>Output:</strong> PracticeHard
<strong>Explanation: </strong>Combined "Practice" and "Hard"</span></pre>

<p>&nbsp;</p>

<p><span style="font-size:18px"><strong>Your Task: &nbsp;</strong><br>
You dont need to read input or print anything. Complete the function <strong>conCat()</strong>&nbsp;which accepts two strings S1 and S2 as input parameter and returns concatenated string.</span></p>

<p><br>
<span style="font-size:18px"><strong>Expected Time Complexity: </strong>O(|S1| + |S2|) .<br>
<strong>Expected Auxiliary Space: </strong>O(|S1| + |S2|) .<br>
where N is the length of a&nbsp;String</span></p>

<p><br>
<span style="font-size:18px"><strong>Constraints:</strong><br>
1 &lt;= |S1| , |S2|&nbsp;&lt;= 10<sup>5</sup></span><br>
<span style="font-size:18px">|S| denotes the length of the string S.</span></p>
</div>

---




```cpp
//{ Driver Code Starts
#include<iostream>
#include<string>
using namespace std;

string conCat(string a , string b);

int main()
{
    int t;
    cin>>t;
    while(t--)
    {
        string a,b;
        cin>>a>>b;
        cout<<conCat(a,b)<<endl;
    }
    return 0;
}

// } Driver Code Ends


string conCat(string s1 , string s2)
{
    // code here.
    return s1+s2;
}

```
