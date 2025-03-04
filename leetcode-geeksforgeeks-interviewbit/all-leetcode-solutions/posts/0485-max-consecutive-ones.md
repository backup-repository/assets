---
title: 0485 Max Consecutive Ones
summary: 0485 Max Consecutive Ones LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "0485 Max Consecutive Ones LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0485 Max Consecutive Ones - Solution Explained/problem-solving.webp
    alt: 0485 Max Consecutive Ones
    hiddenInList: true
    hiddenInSingle: false
---


# [485. Max Consecutive Ones](https://leetcode.com/problems/max-consecutive-ones)


## Description

<p>Given a binary array <code>nums</code>, return <em>the maximum number of consecutive </em><code>1</code><em>&#39;s in the array</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,1,0,1,1,1]
<strong>Output:</strong> 3
<strong>Explanation:</strong> The first two digits or the last three digits are consecutive 1s. The maximum number of consecutive 1s is 3.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,0,1,1,0,1]
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>nums[i]</code> is either <code>0</code> or <code>1</code>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def findMaxConsecutiveOnes(self, nums: List[int]) -> int:
        cnt = ans = 0
        for v in nums:
            if v == 1:
                cnt += 1
            else:
                ans = max(ans, cnt)
                cnt = 0
        return max(ans, cnt)
```

```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int cnt = 0, ans = 0;
        for (int v : nums) {
            if (v == 1) {
                ++cnt;
            } else {
                ans = Math.max(ans, cnt);
                cnt = 0;
            }
        }
        return Math.max(cnt, ans);
    }
}
```

```cpp
class Solution {
public:
    int findMaxConsecutiveOnes(vector<int>& nums) {
        int cnt = 0, ans = 0;
        for (int v : nums) {
            if (v == 1) {
                ++cnt;
            } else {
                ans = max(ans, cnt);
                cnt = 0;
            }
        }
        return max(ans, cnt);
    }
};
```

```go
func findMaxConsecutiveOnes(nums []int) int {
	ans, cnt := 0, 0
	for _, v := range nums {
		if v == 1 {
			cnt++
		} else {
			ans = max(ans, cnt)
			cnt = 0
		}
	}
	return max(ans, cnt)
}
```

```ts
function findMaxConsecutiveOnes(nums: number[]): number {
    let res = 0;
    let count = 0;
    for (const num of nums) {
        if (num === 0) {
            res = Math.max(res, count);
            count = 0;
        } else {
            count++;
        }
    }
    return Math.max(res, count);
}
```

```rust
impl Solution {
    pub fn find_max_consecutive_ones(nums: Vec<i32>) -> i32 {
        let mut res = 0;
        let mut count = 0;
        for num in nums {
            if num == 0 {
                res = res.max(count);
                count = 0;
            } else {
                count += 1;
            }
        }
        res.max(count)
    }
}
```

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var findMaxConsecutiveOnes = function (nums) {
    let res = 0,
        t = 0;
    for (let num of nums) {
        if (num == 1) {
            ++t;
        } else {
            res = Math.max(res, t);
            t = 0;
        }
    }
    return Math.max(res, t);
};
```

```php
class Solution {
    /**
     * @param Integer[] $nums
     * @return Integer
     */
    function findMaxConsecutiveOnes($nums) {
        $tmp = $max = 0;
        for ($i = 0; $i < count($nums); $i++) {
            if ($nums[$i] == 1) {
                $tmp++;
            } else {
                $max = max($tmp, $max);
                $tmp = 0;
            }
        }
        return max($tmp, $max);
    }
}
```

<!-- tabs:end -->

<!-- end -->
