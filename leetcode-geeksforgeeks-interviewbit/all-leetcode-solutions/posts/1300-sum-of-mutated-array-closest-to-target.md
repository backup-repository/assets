---
title: 1300 Sum Of Mutated Array Closest To Target
summary: 1300 Sum Of Mutated Array Closest To Target LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1300 Sum Of Mutated Array Closest To Target LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1300 Sum Of Mutated Array Closest To Target - Solution Explained/problem-solving.webp
    alt: 1300 Sum Of Mutated Array Closest To Target
    hiddenInList: true
    hiddenInSingle: false
---


# [1300. Sum of Mutated Array Closest to Target](https://leetcode.com/problems/sum-of-mutated-array-closest-to-target)


## Description

<p>Given an integer array <code>arr</code> and a target value <code>target</code>, return the integer <code>value</code> such that when we change all the integers larger than <code>value</code> in the given array to be equal to <code>value</code>, the sum of the array gets as close as possible (in absolute difference) to <code>target</code>.</p>

<p>In case of a tie, return the minimum such integer.</p>

<p>Notice that the answer is not neccesarilly a number from <code>arr</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr = [4,9,3], target = 10
<strong>Output:</strong> 3
<strong>Explanation:</strong> When using 3 arr converts to [3, 3, 3] which sums 9 and that&#39;s the optimal answer.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr = [2,3,5], target = 10
<strong>Output:</strong> 5
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> arr = [60864,25176,27249,21296,20204], target = 56803
<strong>Output:</strong> 11361
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= arr[i], target &lt;= 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def findBestValue(self, arr: List[int], target: int) -> int:
        arr.sort()
        s = list(accumulate(arr, initial=0))
        ans, diff = 0, inf
        for value in range(max(arr) + 1):
            i = bisect_right(arr, value)
            d = abs(s[i] + (len(arr) - i) * value - target)
            if diff > d:
                diff = d
                ans = value
        return ans
```

```java
class Solution {
    public int findBestValue(int[] arr, int target) {
        Arrays.sort(arr);
        int n = arr.length;
        int[] s = new int[n + 1];
        int mx = 0;
        for (int i = 0; i < n; ++i) {
            s[i + 1] = s[i] + arr[i];
            mx = Math.max(mx, arr[i]);
        }
        int ans = 0, diff = 1 << 30;
        for (int value = 0; value <= mx; ++value) {
            int i = search(arr, value);
            int d = Math.abs(s[i] + (n - i) * value - target);
            if (diff > d) {
                diff = d;
                ans = value;
            }
        }
        return ans;
    }

    private int search(int[] arr, int x) {
        int left = 0, right = arr.length;
        while (left < right) {
            int mid = (left + right) >> 1;
            if (arr[mid] > x) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left;
    }
}
```

```cpp
class Solution {
public:
    int findBestValue(vector<int>& arr, int target) {
        sort(arr.begin(), arr.end());
        int n = arr.size();
        int s[n + 1];
        s[0] = 0;
        int mx = 0;
        for (int i = 0; i < n; ++i) {
            s[i + 1] = s[i] + arr[i];
            mx = max(mx, arr[i]);
        }
        int ans = 0, diff = 1 << 30;
        for (int value = 0; value <= mx; ++value) {
            int i = upper_bound(arr.begin(), arr.end(), value) - arr.begin();
            int d = abs(s[i] + (n - i) * value - target);
            if (diff > d) {
                diff = d;
                ans = value;
            }
        }
        return ans;
    }
};
```

```go
func findBestValue(arr []int, target int) (ans int) {
	sort.Ints(arr)
	n := len(arr)
	s := make([]int, n+1)
	mx := slices.Max(arr)
	for i, x := range arr {
		s[i+1] = s[i] + x
	}
	diff := 1 << 30
	for value := 0; value <= mx; value++ {
		i := sort.SearchInts(arr, value+1)
		d := abs(s[i] + (n-i)*value - target)
		if diff > d {
			diff = d
			ans = value
		}
	}
	return
}

func abs(x int) int {
	if x < 0 {
		return -x
	}
	return x
}
```

<!-- tabs:end -->

<!-- end -->
