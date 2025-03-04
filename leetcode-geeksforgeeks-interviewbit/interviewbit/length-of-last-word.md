---
title: Length Of Last Word
summary: Length Of Last Word - Interviewbit Solution Explained
date: 2020-06-20
tags: [interviewbit]
series: [interviewbit]
keywords: ["interviewbit", "interviewbit solution in Python3 C++ Java", "Length Of Last Word Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Length Of Last Word - Solution Explained/problem-solving.webp
    alt: Length Of Last Word
    hiddenInList: true
    hiddenInSingle: false
---

# Length Of Last Word

https://www.interviewbit.com/problems/length-of-last-word



hint1

Not using library functions and traversing the string only once is the main twist here.

Try to answer these questions while using single loop:
How can you detect the end of the string? 
How can you detect where the word begins?

hint2

As said before, this problem does not allow using library functions.

What if you maintained the length of the current word?

You reset the length of the word when the next word begins (When does a new word begin?)

Return the last length you have.

## Solution

```cpp

/* editorial */

int Solution::lengthOfLastWord(const string A) {
    const char * s = A.c_str();
    int len = 0;
    while (*s) {
        if (*s != ' ') {
            len++;
            s++;
            continue;
        }
        s++;
        if (*s && *s != ' ')
            len = 0;
    }
    return len;
}

/* my solution */

int Solution::lengthOfLastWord(const string A) {
    int n = A.length();
    if (n == 0)
        return 0;

    int i = n - 1;
    while (i != 0 && A[i] == ' ')
        i--;

    int count = 0;
    while (A[i] != ' ') {
        count++;
        i--;
        if (i < 0)
            break;
    }

    return count;
}
```