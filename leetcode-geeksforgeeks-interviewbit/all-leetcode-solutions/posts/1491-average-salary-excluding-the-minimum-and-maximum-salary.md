---
title: 1491 Average Salary Excluding The Minimum And Maximum Salary
summary: 1491 Average Salary Excluding The Minimum And Maximum Salary LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1491 Average Salary Excluding The Minimum And Maximum Salary LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1491 Average Salary Excluding The Minimum And Maximum Salary - Solution Explained/problem-solving.webp
    alt: 1491 Average Salary Excluding The Minimum And Maximum Salary
    hiddenInList: true
    hiddenInSingle: false
---


# [1491. Average Salary Excluding the Minimum and Maximum Salary](https://leetcode.com/problems/average-salary-excluding-the-minimum-and-maximum-salary)


## Description

<p>You are given an array of <strong>unique</strong> integers <code>salary</code> where <code>salary[i]</code> is the salary of the <code>i<sup>th</sup></code> employee.</p>

<p>Return <em>the average salary of employees excluding the minimum and maximum salary</em>. Answers within <code>10<sup>-5</sup></code> of the actual answer will be accepted.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> salary = [4000,3000,1000,2000]
<strong>Output:</strong> 2500.00000
<strong>Explanation:</strong> Minimum salary and maximum salary are 1000 and 4000 respectively.
Average salary excluding minimum and maximum salary is (2000+3000) / 2 = 2500
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> salary = [1000,2000,3000]
<strong>Output:</strong> 2000.00000
<strong>Explanation:</strong> Minimum salary and maximum salary are 1000 and 3000 respectively.
Average salary excluding minimum and maximum salary is (2000) / 1 = 2000
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= salary.length &lt;= 100</code></li>
	<li><code>1000 &lt;= salary[i] &lt;= 10<sup>6</sup></code></li>
	<li>All the integers of <code>salary</code> are <strong>unique</strong>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def average(self, salary: List[int]) -> float:
        s = sum(salary) - min(salary) - max(salary)
        return s / (len(salary) - 2)
```

```java
class Solution {
    public double average(int[] salary) {
        int s = 0;
        int mi = 10000000, mx = 0;
        for (int v : salary) {
            mi = Math.min(mi, v);
            mx = Math.max(mx, v);
            s += v;
        }
        s -= (mi + mx);
        return s * 1.0 / (salary.length - 2);
    }
}
```

```cpp
class Solution {
public:
    double average(vector<int>& salary) {
        int s = 0;
        int mi = 1e7, mx = 0;
        for (int v : salary) {
            s += v;
            mi = min(mi, v);
            mx = max(mx, v);
        }
        s -= (mi + mx);
        return (double) s / (salary.size() - 2);
    }
};
```

```go
func average(salary []int) float64 {
	s := 0
	mi, mx := 10000000, 0
	for _, v := range salary {
		s += v
		mi = min(mi, v)
		mx = max(mx, v)
	}
	s -= (mi + mx)
	return float64(s) / float64(len(salary)-2)
}
```

```ts
function average(salary: number[]): number {
    let max = -Infinity;
    let min = Infinity;
    let sum = 0;
    for (const v of salary) {
        sum += v;
        max = Math.max(max, v);
        min = Math.min(min, v);
    }
    return (sum - max - min) / (salary.length - 2);
}
```

```rust
impl Solution {
    pub fn average(salary: Vec<i32>) -> f64 {
        let n = salary.len() as i32;
        let mut min = i32::MAX;
        let mut max = i32::MIN;
        let mut sum = 0;
        for &num in salary.iter() {
            min = min.min(num);
            max = max.max(num);
            sum += num;
        }
        f64::from(sum - min - max) / f64::from(n - 2)
    }
}
```

```php
class Solution {
    /**
     * @param Integer[] $salary
     * @return Float
     */
    function average($salary) {
        $max = $sum = 0;
        $min = 10 ** 6;
        for ($i = 0; $i < count($salary); $i++) {
            $min = min($min, $salary[$i]);
            $max = max($max, $salary[$i]);
            $sum += $salary[$i];
        }
        return ($sum - $max - $min) / (count($salary) - 2);
    }
}
```

```c
#define max(a, b) (((a) > (b)) ? (a) : (b))
#define min(a, b) (((a) < (b)) ? (a) : (b))

double average(int* salary, int salarySize) {
    int ma = INT_MIN;
    int mi = INT_MAX;
    int sum = 0;
    for (int i = 0; i < salarySize; i++) {
        sum += salary[i];
        ma = max(ma, salary[i]);
        mi = min(mi, salary[i]);
    }
    return (sum - mi - ma) * 1.0 / (salarySize - 2);
}
```

<!-- tabs:end -->

<!-- end -->
