---
title: Min Stack
summary: Min Stack - Interviewbit Solution Explained
date: 2020-06-20
tags: [interviewbit]
series: [interviewbit]
keywords: ["interviewbit", "interviewbit solution in Python3 C++ Java", "Min Stack Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Min Stack - Solution Explained/problem-solving.webp
    alt: Min Stack
    hiddenInList: true
    hiddenInSingle: false
---

# Min Stack

https://www.interviewbit.com/problems/min-stack



What if you maintaned the current minimum in a variable and only stored
the places where the minimum changes or the element is same as the minimum.

pop() becomes a little trickier in such a case. 
You only pop() from the min stack if the top() of min stack is same as the current minimum.

Space complexity: O(N + X) where X = number of places where minimum changes or the element is same as the minimum

## Solution

```cpp

vector<int> v, v1;

MinStack::MinStack() {
    v.clear();
    v1.clear();
}

void MinStack::push(int x) {
    v.push_back(x);
    if (v1.empty() || x <= v1.back()) v1.push_back(x);
}

void MinStack::pop() {
    if (!v.empty()) {
        if (v.back() == v1.back()) v1.pop_back();
        v.pop_back();
    }
}

int MinStack::top() {
    if (!v.empty())
        return v.back();
    else
        return -1;
}

int MinStack::getMin() {
    if (!v1.empty())
        return v1.back();
    else
        return -1;
}
```