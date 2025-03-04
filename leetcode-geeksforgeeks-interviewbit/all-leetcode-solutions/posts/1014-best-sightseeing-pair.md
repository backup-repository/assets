---
title: 1014 Best Sightseeing Pair
summary: 1014 Best Sightseeing Pair LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1014 Best Sightseeing Pair LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1014 Best Sightseeing Pair - Solution Explained/problem-solving.webp
    alt: 1014 Best Sightseeing Pair
    hiddenInList: true
    hiddenInSingle: false
---


# [1014. Best Sightseeing Pair](https://leetcode.com/problems/best-sightseeing-pair)


## Description

<p>You are given an integer array <code>values</code> where values[i] represents the value of the <code>i<sup>th</sup></code> sightseeing spot. Two sightseeing spots <code>i</code> and <code>j</code> have a <strong>distance</strong> <code>j - i</code> between them.</p>

<p>The score of a pair (<code>i &lt; j</code>) of sightseeing spots is <code>values[i] + values[j] + i - j</code>: the sum of the values of the sightseeing spots, minus the distance between them.</p>

<p>Return <em>the maximum score of a pair of sightseeing spots</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> values = [8,1,5,2,6]
<strong>Output:</strong> 11
<strong>Explanation:</strong> i = 0, j = 2, values[i] + values[j] + i - j = 8 + 5 + 0 - 2 = 11
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> values = [1,2]
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= values.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= values[i] &lt;= 1000</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def maxScoreSightseeingPair(self, values: List[int]) -> int:
        ans, mx = 0, values[0]
        for j in range(1, len(values)):
            ans = max(ans, values[j] - j + mx)
            mx = max(mx, values[j] + j)
        return ans
```

```java
class Solution {
    public int maxScoreSightseeingPair(int[] values) {
        int ans = 0, mx = values[0];
        for (int j = 1; j < values.length; ++j) {
            ans = Math.max(ans, values[j] - j + mx);
            mx = Math.max(mx, values[j] + j);
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int maxScoreSightseeingPair(vector<int>& values) {
        int ans = 0, mx = values[0];
        for (int j = 1; j < values.size(); ++j) {
            ans = max(ans, values[j] - j + mx);
            mx = max(mx, values[j] + j);
        }
        return ans;
    }
};
```

```go
func maxScoreSightseeingPair(values []int) (ans int) {
	for j, mx := 1, values[0]; j < len(values); j++ {
		ans = max(ans, values[j]-j+mx)
		mx = max(mx, values[j]+j)
	}
	return
}
```

```ts
function maxScoreSightseeingPair(values: number[]): number {
    let ans = 0;
    let mx = values[0];
    for (let j = 1; j < values.length; ++j) {
        ans = Math.max(ans, values[j] - j + mx);
        mx = Math.max(mx, values[j] + j);
    }
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
