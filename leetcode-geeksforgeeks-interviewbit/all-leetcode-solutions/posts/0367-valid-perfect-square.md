---
title: 0367 Valid Perfect Square
summary: 0367 Valid Perfect Square LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "0367 Valid Perfect Square LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0367 Valid Perfect Square - Solution Explained/problem-solving.webp
    alt: 0367 Valid Perfect Square
    hiddenInList: true
    hiddenInSingle: false
---


# [367. Valid Perfect Square](https://leetcode.com/problems/valid-perfect-square)


## Description

<p>Given a positive integer num, return <code>true</code> <em>if</em> <code>num</code> <em>is a perfect square or</em> <code>false</code> <em>otherwise</em>.</p>

<p>A <strong>perfect square</strong> is an integer that is the square of an integer. In other words, it is the product of some integer with itself.</p>

<p>You must not use any built-in library function, such as <code>sqrt</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> num = 16
<strong>Output:</strong> true
<strong>Explanation:</strong> We return true because 4 * 4 = 16 and 4 is an integer.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> num = 14
<strong>Output:</strong> false
<strong>Explanation:</strong> We return false because 3.742 * 3.742 = 14 and 3.742 is not an integer.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= num &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

## Solutions

### Solution 1: Binary search

<!-- tabs:start -->

```python
class Solution:
    def isPerfectSquare(self, num: int) -> bool:
        left, right = 1, num
        while left < right:
            mid = (left + right) >> 1
            if mid * mid >= num:
                right = mid
            else:
                left = mid + 1
        return left * left == num
```

```java
class Solution {
    public boolean isPerfectSquare(int num) {
        long left = 1, right = num;
        while (left < right) {
            long mid = (left + right) >>> 1;
            if (mid * mid >= num) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left * left == num;
    }
}
```

```cpp
class Solution {
public:
    bool isPerfectSquare(int num) {
        long left = 1, right = num;
        while (left < right) {
            long mid = left + right >> 1;
            if (mid * mid >= num)
                right = mid;
            else
                left = mid + 1;
        }
        return left * left == num;
    }
};
```

```go
func isPerfectSquare(num int) bool {
	left, right := 1, num
	for left < right {
		mid := (left + right) >> 1
		if mid*mid >= num {
			right = mid
		} else {
			left = mid + 1
		}
	}
	return left*left == num
}
```

```ts
function isPerfectSquare(num: number): boolean {
    let left = 1;
    let right = num >> 1;
    while (left < right) {
        const mid = (left + right) >>> 1;
        if (mid * mid < num) {
            left = mid + 1;
        } else {
            right = mid;
        }
    }
    return left * left === num;
}
```

```rust
use std::cmp::Ordering;
impl Solution {
    pub fn is_perfect_square(num: i32) -> bool {
        let num: i64 = num as i64;
        let mut left = 1;
        let mut right = num >> 1;
        while left < right {
            let mid = left + (right - left) / 2;
            match (mid * mid).cmp(&num) {
                Ordering::Less => {
                    left = mid + 1;
                }
                Ordering::Greater => {
                    right = mid - 1;
                }
                Ordering::Equal => {
                    return true;
                }
            }
        }
        left * left == num
    }
}
```

<!-- tabs:end -->

### Solution 2: Math trick

This is a math problem：

```bash
1 = 1
4 = 1 + 3
9 = 1 + 3 + 5
16 = 1 + 3 + 5 + 7
25 = 1 + 3 + 5 + 7 + 9
36 = 1 + 3 + 5 + 7 + 9 + 11
....
so 1+3+...+(2n-1) = (2n-1 + 1)n/2 = n²
```

<!-- tabs:start -->

```python
class Solution:
    def isPerfectSquare(self, num: int) -> bool:
        i = 1
        while num > 0:
            num -= i
            i += 2
        return num == 0
```

```java
class Solution {
    public boolean isPerfectSquare(int num) {
        for (int i = 1; num > 0; i += 2) {
            num -= i;
        }
        return num == 0;
    }
}
```

```cpp
class Solution {
public:
    bool isPerfectSquare(int num) {
        for (int i = 1; num > 0; i += 2) num -= i;
        return num == 0;
    }
};
```

```go
func isPerfectSquare(num int) bool {
	for i := 1; num > 0; i += 2 {
		num -= i
	}
	return num == 0
}
```

```ts
function isPerfectSquare(num: number): boolean {
    let i = 1;
    while (num > 0) {
        num -= i;
        i += 2;
    }
    return num === 0;
}
```

```rust
impl Solution {
    pub fn is_perfect_square(mut num: i32) -> bool {
        let mut i = 1;
        while num > 0 {
            num -= i;
            i += 2;
        }
        num == 0
    }
}
```

<!-- tabs:end -->

<!-- end -->
