---
title: Number Of Divisors
summary: Number Of Divisors - GeeksforGeeks Solution Explained
date: 2020-06-20
tags: [geeksforgeeks]
series: [GeeksforGeeks]
keywords: ["GeeksforGeeks", "GeeksforGeeks solution in Python3 C++ Java", "Number Of Divisors Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Number Of Divisors - Solution Explained/problem-solving.webp
    alt: Number Of Divisors
    hiddenInList: true
    hiddenInSingle: false
---


# Number of divisors
## Easy
<div class="problem-statement">
                <p></p><p><span style="font-size:18px">Given&nbsp;an integer <strong>N,</strong> find&nbsp;the number of divisors of N that are divisible by 3.</span><br>
&nbsp;</p>

<p><span style="font-size:18px"><strong>Example 1:</strong></span></p>

<pre><span style="font-size:18px"><strong>Input : </strong>6
<strong>Output: </strong>2
<strong>Explanation: </strong>1, 2, 3, 6 are divisors 
of 6 out of which 3 and 6 are divisible 
by 3.
</span>
</pre>

<p><span style="font-size:18px"><strong>Example 2:</strong></span></p>

<pre><span style="font-size:18px"><strong>Input: </strong>10
<strong>Output: </strong>0
<strong>Explanation: </strong>1, 2, 5 and 10 are divisors 
of 10 but none of them are divisible by 3.</span>
</pre>

<p>&nbsp;</p>

<p><span style="font-size:18px"><strong>Your Task:</strong></span></p>

<p><span style="font-size:18px">You don't need to read or print anything. Your task is to complete the function&nbsp;<strong>count_divisors()</strong>&nbsp;which takes N as input parameter and returns count of divisor which are divisible by 3.</span><br>
&nbsp;</p>

<p><span style="font-size:18px"><strong>Expected Time Complexity:&nbsp;</strong>O(sqrt(N))<br>
<strong>Expected Space Complexity: </strong>O(1)</span><br>
&nbsp;</p>

<p><span style="font-size:18px"><strong>Constraints:</strong><br>
1 &lt;= N &lt;= 10<sup>5</sup></span></p>
 <p></p>
            </div>

---




```cpp
// { Driver Code Starts
//Initial Template for C++


#include<bits/stdc++.h>
using namespace std;

 // } Driver Code Ends
//User function Template for C++

class Solution
{
	public:
		int count_divisors(int n)
		{
		    //Code here.
		    int count=0;
 if(n<3)
 {return 0;}
 if(n%3==0)
 {count=1;}
 if(n%3!=0)
 {return 0;}
 
     for(int i=3;i<=n/2;i=i+3)
     {if(n%i==0)
         {count++;}
     }
  return count;
		}
};

// { Driver Code Starts.
int main(){
    int T;
    cin >> T;
    while(T--)
    {
    	int n;
    	cin >> n;
    	Solution ob;
    	int ans = ob.count_divisors(n);
    	cout << ans << "\n";
    }
	return 0;
}  // } Driver Code Ends
```
