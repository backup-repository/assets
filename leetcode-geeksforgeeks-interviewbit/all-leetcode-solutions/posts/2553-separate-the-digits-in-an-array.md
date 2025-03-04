---
title: 2553 Separate The Digits In An Array
summary: 2553 Separate The Digits In An Array LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "2553 Separate The Digits In An Array LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2553 Separate The Digits In An Array - Solution Explained/problem-solving.webp
    alt: 2553 Separate The Digits In An Array
    hiddenInList: true
    hiddenInSingle: false
---


# [2553. Separate the Digits in an Array](https://leetcode.com/problems/separate-the-digits-in-an-array)


## Description

<p>Given an array of positive integers <code>nums</code>, return <em>an array </em><code>answer</code><em> that consists of the digits of each integer in </em><code>nums</code><em> after separating them in <strong>the same order</strong> they appear in </em><code>nums</code>.</p>

<p>To separate the digits of an integer is to get all the digits it has in the same order.</p>

<ul>
	<li>For example, for the integer <code>10921</code>, the separation of its digits is <code>[1,0,9,2,1]</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [13,25,83,77]
<strong>Output:</strong> [1,3,2,5,8,3,7,7]
<strong>Explanation:</strong> 
- The separation of 13 is [1,3].
- The separation of 25 is [2,5].
- The separation of 83 is [8,3].
- The separation of 77 is [7,7].
answer = [1,3,2,5,8,3,7,7]. Note that answer contains the separations in the same order.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [7,1,3,9]
<strong>Output:</strong> [7,1,3,9]
<strong>Explanation:</strong> The separation of each integer in nums is itself.
answer = [7,1,3,9].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 1000</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1: Simulation

Split each number in the array into digits, then put the split numbers into the answer array in order.

The time complexity is $O(n \times \log_{10} M)$, and the space complexity is $O(n \times \log_{10} M)$. Where $n$ is the length of the array $nums$, and $M$ is the maximum value in the array $nums$.

<!-- tabs:start -->

```python
class Solution:
    def separateDigits(self, nums: List[int]) -> List[int]:
        ans = []
        for x in nums:
            t = []
            while x:
                t.append(x % 10)
                x //= 10
            ans.extend(t[::-1])
        return ans
```

```java
class Solution {
    public int[] separateDigits(int[] nums) {
        List<Integer> res = new ArrayList<>();
        for (int x : nums) {
            List<Integer> t = new ArrayList<>();
            for (; x > 0; x /= 10) {
                t.add(x % 10);
            }
            Collections.reverse(t);
            res.addAll(t);
        }
        int[] ans = new int[res.size()];
        for (int i = 0; i < ans.length; ++i) {
            ans[i] = res.get(i);
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    vector<int> separateDigits(vector<int>& nums) {
        vector<int> ans;
        for (int x : nums) {
            vector<int> t;
            for (; x; x /= 10) {
                t.push_back(x % 10);
            }
            while (t.size()) {
                ans.push_back(t.back());
                t.pop_back();
            }
        }
        return ans;
    }
};
```

```go
func separateDigits(nums []int) (ans []int) {
	for _, x := range nums {
		t := []int{}
		for ; x > 0; x /= 10 {
			t = append(t, x%10)
		}
		for i, j := 0, len(t)-1; i < j; i, j = i+1, j-1 {
			t[i], t[j] = t[j], t[i]
		}
		ans = append(ans, t...)
	}
	return
}
```

```ts
function separateDigits(nums: number[]): number[] {
    const ans: number[] = [];
    for (let num of nums) {
        const t: number[] = [];
        while (num) {
            t.push(num % 10);
            num = Math.floor(num / 10);
        }
        ans.push(...t.reverse());
    }
    return ans;
}
```

```rust
impl Solution {
    pub fn separate_digits(nums: Vec<i32>) -> Vec<i32> {
        let mut ans = Vec::new();
        for &num in nums.iter() {
            let mut num = num;
            let mut t = Vec::new();
            while num != 0 {
                t.push(num % 10);
                num /= 10;
            }
            t.into_iter()
                .rev()
                .for_each(|v| ans.push(v));
        }
        ans
    }
}
```

```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* separateDigits(int* nums, int numsSize, int* returnSize) {
    int n = 0;
    for (int i = 0; i < numsSize; i++) {
        int t = nums[i];
        while (t != 0) {
            t /= 10;
            n++;
        }
    }
    int* ans = malloc(sizeof(int) * n);
    for (int i = numsSize - 1, j = n - 1; i >= 0; i--) {
        int t = nums[i];
        while (t != 0) {
            ans[j--] = t % 10;
            t /= 10;
        }
    }
    *returnSize = n;
    return ans;
}
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```rust
impl Solution {
    pub fn separate_digits(nums: Vec<i32>) -> Vec<i32> {
        let mut ans = vec![];

        for n in nums {
            let mut t = vec![];
            let mut x = n;

            while x != 0 {
                t.push(x % 10);
                x /= 10;
            }

            for i in (0..t.len()).rev() {
                ans.push(t[i]);
            }
        }

        ans
    }
}
```

<!-- tabs:end -->

<!-- end -->
