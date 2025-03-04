---
title: Numbers Of Length N And Value Less Than K
summary: Numbers Of Length N And Value Less Than K - Interviewbit Solution Explained
date: 2020-06-20
tags: [interviewbit]
series: [interviewbit]
keywords: ["interviewbit", "interviewbit solution in Python3 C++ Java", "Numbers Of Length N And Value Less Than K Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Numbers Of Length N And Value Less Than K - Solution Explained/problem-solving.webp
    alt: Numbers Of Length N And Value Less Than K
    hiddenInList: true
    hiddenInSingle: false
---

# Numbers Of Length N and Value Less Than K

https://www.interviewbit.com/problems/numbers-of-length-n-and-value-less-than-k


## Solution

```cpp
vector <int> numToVec(int N) {   
    vector<int> digit;
    while(N != 0) {
        digit.push_back(N % 10);
        N = N / 10;
    }
    if(digit.size() == 0)
        digit.push_back(0);

    reverse(digit.begin(), digit.end());
    return digit; 
}

int Solution:: solve(vector<int> &A, int B, int C) {
    vector<int> digit;
    int  d, d2;
    // Convert number to digit array
    digit = numToVec(C);
    d = A.size();

    //Case 1
    if(B > digit.size()  || d == 0)
        return 0;

    // Case 2
    else if(B < digit.size()) {
        // contain 0
        if(A[0] == 0 && B != 1)
            return (d - 1) * pow(d, B - 1);
        else 
            return pow(d, B);
    }

    //Case 3
    else {
          int dp[B + 1], lower[11];
          for(int i = 0; i <= B; i++)
              dp[i] = 0;
          for(int i = 0; i <= 10; i++)
              lower[i] = 0;
          for(int i = 0; i < d; i++)
              lower[A[i] + 1] = 1;

          for(int i = 1; i <= 10; i++)
              lower[i] = lower[i-1] + lower[i]; 

          bool flag = true;
          dp[0] = 0;
          for(int i = 1; i <= B; i++) {
              d2 = lower[digit[i-1]];
              dp[i] = dp[i-1] * d;

              // For first index we can't use 0
             if(i == 1 &&  A[0] == 0 && B != 1)
                 d2 = d2 - 1;

             //Whether (i-1) digit of generated number can be equal to (i - 1) digit of C.
             if(flag)
                 dp[i] += d2;
             //Is digit[i - 1] present in A ?
                flag = flag & (lower[digit[i-1] + 1] == lower[digit[i-1]] + 1);
        }
    return dp[B];                   
    } 
}

/*

-------
(not working)

int baseconv(vector<int> &A, int x, int len) {
    int i = 0;
    int n = A.size();
    x++;
    int res = 0;
    do {
        x--;
        int digit = A[x % n];
        res = res * 10 + digit;
        x /= n;
    } while (x);
    return res;
}

int Solution::solve(vector<int> &A, int B, int C) {
    int counter = 0;
    
    int n = A.size();
    
    if (n==0)
        return 0;
        
    int limit = pow(10, B);
        
        
    // base = [a,b,c,..]
    // counter = 0 -> x = aa
    // counter = 1 -> x = ab
    
    for (counter=0; counter<10; counter++) {
        int x = baseconv(A, counter, B);
        cout << counter << ": " << x << endl;
    }
    

    while (x<C && x<limit) {
        x = baseconv(A, counter, B);
        counter++;
    }
    
    return counter;
}


*/



```