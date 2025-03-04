---
title: 2208 Minimum Operations To Halve Array Sum
summary: 2208 Minimum Operations To Halve Array Sum LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "2208 Minimum Operations To Halve Array Sum LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2208 Minimum Operations To Halve Array Sum - Solution Explained/problem-solving.webp
    alt: 2208 Minimum Operations To Halve Array Sum
    hiddenInList: true
    hiddenInSingle: false
---


# [2208. Minimum Operations to Halve Array Sum](https://leetcode.com/problems/minimum-operations-to-halve-array-sum)


## Description

<p>You are given an array <code>nums</code> of positive integers. In one operation, you can choose <strong>any</strong> number from <code>nums</code> and reduce it to <strong>exactly</strong> half the number. (Note that you may choose this reduced number in future operations.)</p>

<p>Return<em> the <strong>minimum</strong> number of operations to reduce the sum of </em><code>nums</code><em> by <strong>at least</strong> half.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [5,19,8,1]
<strong>Output:</strong> 3
<strong>Explanation:</strong> The initial sum of nums is equal to 5 + 19 + 8 + 1 = 33.
The following is one of the ways to reduce the sum by at least half:
Pick the number 19 and reduce it to 9.5.
Pick the number 9.5 and reduce it to 4.75.
Pick the number 8 and reduce it to 4.
The final array is [5, 4.75, 4, 1] with a total sum of 5 + 4.75 + 4 + 1 = 14.75. 
The sum of nums has been reduced by 33 - 14.75 = 18.25, which is at least half of the initial sum, 18.25 &gt;= 33/2 = 16.5.
Overall, 3 operations were used so we return 3.
It can be shown that we cannot reduce the sum by at least half in less than 3 operations.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,8,20]
<strong>Output:</strong> 3
<strong>Explanation:</strong> The initial sum of nums is equal to 3 + 8 + 20 = 31.
The following is one of the ways to reduce the sum by at least half:
Pick the number 20 and reduce it to 10.
Pick the number 10 and reduce it to 5.
Pick the number 3 and reduce it to 1.5.
The final array is [1.5, 8, 5] with a total sum of 1.5 + 8 + 5 = 14.5. 
The sum of nums has been reduced by 31 - 14.5 = 16.5, which is at least half of the initial sum, 16.5 &gt;= 31/2 = 15.5.
Overall, 3 operations were used so we return 3.
It can be shown that we cannot reduce the sum by at least half in less than 3 operations.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>7</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def halveArray(self, nums: List[int]) -> int:
        s = sum(nums) / 2
        h = []
        for v in nums:
            heappush(h, -v)
        ans = 0
        while s > 0:
            t = -heappop(h) / 2
            s -= t
            heappush(h, -t)
            ans += 1
        return ans
```

```java
class Solution {
    public int halveArray(int[] nums) {
        double s = 0;
        PriorityQueue<Double> q = new PriorityQueue<>(Collections.reverseOrder());
        for (int v : nums) {
            q.offer(v * 1.0);
            s += v;
        }
        s /= 2.0;
        int ans = 0;
        while (s > 0) {
            double t = q.poll();
            s -= t / 2.0;
            q.offer(t / 2.0);
            ++ans;
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int halveArray(vector<int>& nums) {
        priority_queue<double> q;
        double s = 0;
        for (int& v : nums) {
            s += v;
            q.push(v);
        }
        s /= 2.0;
        int ans = 0;
        while (s > 0) {
            double t = q.top() / 2;
            q.pop();
            s -= t;
            q.push(t);
            ++ans;
        }
        return ans;
    }
};
```

```go
func halveArray(nums []int) (ans int) {
	var s float64
	q := hp{}
	for _, x := range nums {
		s += float64(x)
		heap.Push(&q, float64(x))
	}
	s /= 2
	for s > 0 {
		x := heap.Pop(&q).(float64)
		ans++
		s -= x / 2
		heap.Push(&q, x/2)
	}
	return
}

type hp struct{ sort.Float64Slice }

func (h hp) Less(i, j int) bool { return h.Float64Slice[i] > h.Float64Slice[j] }
func (h *hp) Push(v any)        { h.Float64Slice = append(h.Float64Slice, v.(float64)) }
func (h *hp) Pop() any {
	a := h.Float64Slice
	v := a[len(a)-1]
	h.Float64Slice = a[:len(a)-1]
	return v
}
```

```ts
function halveArray(nums: number[]): number {
    let s: number = nums.reduce((a, b) => a + b) / 2;
    const h = new MaxPriorityQueue();
    for (const v of nums) {
        h.enqueue(v, v);
    }
    let ans: number = 0;
    while (s > 0) {
        let { element: t } = h.dequeue();
        t /= 2;
        s -= t;
        h.enqueue(t, t);
        ans += 1;
    }
    return ans;
}
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```go
func halveArray(nums []int) (ans int) {
	half := 0
	for i := range nums {
		nums[i] <<= 20
		half += nums[i]
	}
	h := hp{nums}
	heap.Init(&h)
	for half >>= 1; half > 0; ans++ {
		half -= h.IntSlice[0] >> 1
		h.IntSlice[0] >>= 1
		heap.Fix(&h, 0)
	}
	return
}

type hp struct{ sort.IntSlice }

func (h hp) Less(i, j int) bool { return h.IntSlice[i] > h.IntSlice[j] }
func (hp) Push(any)             {}
func (hp) Pop() (_ any)         { return }
```

<!-- tabs:end -->

<!-- end -->
