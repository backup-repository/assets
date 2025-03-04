---
title: 1387 Sort Integers By The Power Value
summary: 1387 Sort Integers By The Power Value LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1387 Sort Integers By The Power Value LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1387 Sort Integers By The Power Value - Solution Explained/problem-solving.webp
    alt: 1387 Sort Integers By The Power Value
    hiddenInList: true
    hiddenInSingle: false
---


# [1387. Sort Integers by The Power Value](https://leetcode.com/problems/sort-integers-by-the-power-value)


## Description

<p>The power of an integer <code>x</code> is defined as the number of steps needed to transform <code>x</code> into <code>1</code> using the following steps:</p>

<ul>
	<li>if <code>x</code> is even then <code>x = x / 2</code></li>
	<li>if <code>x</code> is odd then <code>x = 3 * x + 1</code></li>
</ul>

<p>For example, the power of <code>x = 3</code> is <code>7</code> because <code>3</code> needs <code>7</code> steps to become <code>1</code> (<code>3 --&gt; 10 --&gt; 5 --&gt; 16 --&gt; 8 --&gt; 4 --&gt; 2 --&gt; 1</code>).</p>

<p>Given three integers <code>lo</code>, <code>hi</code> and <code>k</code>. The task is to sort all integers in the interval <code>[lo, hi]</code> by the power value in <strong>ascending order</strong>, if two or more integers have <strong>the same</strong> power value sort them by <strong>ascending order</strong>.</p>

<p>Return the <code>k<sup>th</sup></code> integer in the range <code>[lo, hi]</code> sorted by the power value.</p>

<p>Notice that for any integer <code>x</code> <code>(lo &lt;= x &lt;= hi)</code> it is <strong>guaranteed</strong> that <code>x</code> will transform into <code>1</code> using these steps and that the power of <code>x</code> is will <strong>fit</strong> in a 32-bit signed integer.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> lo = 12, hi = 15, k = 2
<strong>Output:</strong> 13
<strong>Explanation:</strong> The power of 12 is 9 (12 --&gt; 6 --&gt; 3 --&gt; 10 --&gt; 5 --&gt; 16 --&gt; 8 --&gt; 4 --&gt; 2 --&gt; 1)
The power of 13 is 9
The power of 14 is 17
The power of 15 is 17
The interval sorted by the power value [12,13,14,15]. For k = 2 answer is the second element which is 13.
Notice that 12 and 13 have the same power value and we sorted them in ascending order. Same for 14 and 15.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> lo = 7, hi = 11, k = 4
<strong>Output:</strong> 7
<strong>Explanation:</strong> The power array corresponding to the interval [7, 8, 9, 10, 11] is [16, 3, 19, 6, 14].
The interval sorted by power is [8, 10, 11, 7, 9].
The fourth number in the sorted array is 7.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= lo &lt;= hi &lt;= 1000</code></li>
	<li><code>1 &lt;= k &lt;= hi - lo + 1</code></li>
</ul>

## Solutions

### Solution 1: Custom Sorting

First, we define a function $f(x)$, which represents the number of steps required to change the number $x$ to $1$, i.e., the weight of the number $x$.

Then, we sort all the numbers in the interval $[lo, hi]$ in ascending order of weight. If the weights are the same, we sort them in ascending order of the numbers themselves.

Finally, we return the $k$-th number after sorting.

The time complexity is $O(n \times \log n \times M)$, and the space complexity is $O(n)$. Where $n$ is the number of numbers in the interval $[lo, hi]$, and $M$ is the maximum value of $f(x)$. In this problem, the maximum value of $M$ is $178$.

<!-- tabs:start -->

```python
@cache
def f(x: int) -> int:
    ans = 0
    while x != 1:
        if x % 2 == 0:
            x //= 2
        else:
            x = 3 * x + 1
        ans += 1
    return ans


class Solution:
    def getKth(self, lo: int, hi: int, k: int) -> int:
        return sorted(range(lo, hi + 1), key=f)[k - 1]
```

```java
class Solution {
    public int getKth(int lo, int hi, int k) {
        Integer[] nums = new Integer[hi - lo + 1];
        for (int i = lo; i <= hi; ++i) {
            nums[i - lo] = i;
        }
        Arrays.sort(nums, (a, b) -> {
            int fa = f(a), fb = f(b);
            return fa == fb ? a - b : fa - fb;
        });
        return nums[k - 1];
    }

    private int f(int x) {
        int ans = 0;
        for (; x != 1; ++ans) {
            if (x % 2 == 0) {
                x /= 2;
            } else {
                x = x * 3 + 1;
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int getKth(int lo, int hi, int k) {
        auto f = [](int x) {
            int ans = 0;
            for (; x != 1; ++ans) {
                if (x % 2 == 0) {
                    x /= 2;
                } else {
                    x = 3 * x + 1;
                }
            }
            return ans;
        };
        vector<int> nums;
        for (int i = lo; i <= hi; ++i) {
            nums.push_back(i);
        }
        sort(nums.begin(), nums.end(), [&](int x, int y) {
            int fx = f(x), fy = f(y);
            if (fx != fy) {
                return fx < fy;
            } else {
                return x < y;
            }
        });
        return nums[k - 1];
    }
};
```

```go
func getKth(lo int, hi int, k int) int {
	f := func(x int) (ans int) {
		for ; x != 1; ans++ {
			if x%2 == 0 {
				x /= 2
			} else {
				x = 3*x + 1
			}
		}
		return
	}
	nums := make([]int, hi-lo+1)
	for i := range nums {
		nums[i] = lo + i
	}
	sort.Slice(nums, func(i, j int) bool {
		fx, fy := f(nums[i]), f(nums[j])
		if fx != fy {
			return fx < fy
		}
		return nums[i] < nums[j]
	})
	return nums[k-1]
}
```

```ts
function getKth(lo: number, hi: number, k: number): number {
    const f = (x: number): number => {
        let ans = 0;
        for (; x !== 1; ++ans) {
            if (x % 2 === 0) {
                x >>= 1;
            } else {
                x = x * 3 + 1;
            }
        }
        return ans;
    };
    const nums = new Array(hi - lo + 1).fill(0).map((_, i) => i + lo);
    nums.sort((a, b) => {
        const fa = f(a),
            fb = f(b);
        return fa === fb ? a - b : fa - fb;
    });
    return nums[k - 1];
}
```

<!-- tabs:end -->

<!-- end -->
