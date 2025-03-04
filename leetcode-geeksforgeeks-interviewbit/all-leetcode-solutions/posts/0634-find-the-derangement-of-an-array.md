---
title: 0634 Find The Derangement Of An Array
summary: 0634 Find The Derangement Of An Array LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "0634 Find The Derangement Of An Array LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0634 Find The Derangement Of An Array - Solution Explained/problem-solving.webp
    alt: 0634 Find The Derangement Of An Array
    hiddenInList: true
    hiddenInSingle: false
---


# [634. Find the Derangement of An Array](https://leetcode.com/problems/find-the-derangement-of-an-array)


## Description

<p>In combinatorial mathematics, a <strong>derangement</strong> is a permutation of the elements of a set, such that no element appears in its original position.</p>

<p>You are given an integer <code>n</code>. There is originally an array consisting of <code>n</code> integers from <code>1</code> to <code>n</code> in ascending order, return <em>the number of <strong>derangements</strong> it can generate</em>. Since the answer may be huge, return it <strong>modulo</strong> <code>10<sup>9</sup> + 7</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 3
<strong>Output:</strong> 2
<strong>Explanation:</strong> The original array is [1,2,3]. The two derangements are [2,3,1] and [3,1,2].
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 2
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>6</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def findDerangement(self, n: int) -> int:
        mod = 10**9 + 7
        f = [1] + [0] * n
        for i in range(2, n + 1):
            f[i] = (i - 1) * (f[i - 1] + f[i - 2]) % mod
        return f[n]
```

```java
class Solution {
    public int findDerangement(int n) {
        long[] f = new long[n + 1];
        f[0] = 1;
        final int mod = (int) 1e9 + 7;
        for (int i = 2; i <= n; ++i) {
            f[i] = (i - 1) * (f[i - 1] + f[i - 2]) % mod;
        }
        return (int) f[n];
    }
}
```

```cpp
class Solution {
public:
    int findDerangement(int n) {
        long long f[n + 1];
        memset(f, 0, sizeof(f));
        f[0] = 1;
        const int mod = 1e9 + 7;
        for (int i = 2; i <= n; i++) {
            f[i] = (i - 1LL) * (f[i - 1] + f[i - 2]) % mod;
        }
        return f[n];
    }
};
```

```go
func findDerangement(n int) int {
	f := make([]int, n+1)
	f[0] = 1
	const mod = 1e9 + 7
	for i := 2; i <= n; i++ {
		f[i] = (i - 1) * (f[i-1] + f[i-2]) % mod
	}
	return f[n]
}
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```python
class Solution:
    def findDerangement(self, n: int) -> int:
        mod = 10**9 + 7
        a, b = 1, 0
        for i in range(2, n + 1):
            a, b = b, ((i - 1) * (a + b)) % mod
        return b
```

```java
class Solution {
    public int findDerangement(int n) {
        final int mod = (int) 1e9 + 7;
        long a = 1, b = 0;
        for (int i = 2; i <= n; ++i) {
            long c = (i - 1) * (a + b) % mod;
            a = b;
            b = c;
        }
        return (int) b;
    }
}
```

```cpp
class Solution {
public:
    int findDerangement(int n) {
        long long a = 1, b = 0;
        const int mod = 1e9 + 7;
        for (int i = 2; i <= n; ++i) {
            long long c = (i - 1) * (a + b) % mod;
            a = b;
            b = c;
        }
        return b;
    }
};
```

```go
func findDerangement(n int) int {
	a, b := 1, 0
	const mod = 1e9 + 7
	for i := 2; i <= n; i++ {
		a, b = b, (i-1)*(a+b)%mod
	}
	return b
}
```

<!-- tabs:end -->

<!-- end -->
