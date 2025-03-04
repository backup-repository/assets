---
title: 0728 Self Dividing Numbers
summary: 0728 Self Dividing Numbers LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "0728 Self Dividing Numbers LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0728 Self Dividing Numbers - Solution Explained/problem-solving.webp
    alt: 0728 Self Dividing Numbers
    hiddenInList: true
    hiddenInSingle: false
---


# [728. Self Dividing Numbers](https://leetcode.com/problems/self-dividing-numbers)


## Description

<p>A <strong>self-dividing number</strong> is a number that is divisible by every digit it contains.</p>

<ul>
	<li>For example, <code>128</code> is <strong>a self-dividing number</strong> because <code>128 % 1 == 0</code>, <code>128 % 2 == 0</code>, and <code>128 % 8 == 0</code>.</li>
</ul>

<p>A <strong>self-dividing number</strong> is not allowed to contain the digit zero.</p>

<p>Given two integers <code>left</code> and <code>right</code>, return <em>a list of all the <strong>self-dividing numbers</strong> in the range</em> <code>[left, right]</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> left = 1, right = 22
<strong>Output:</strong> [1,2,3,4,5,6,7,8,9,11,12,15,22]
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> left = 47, right = 85
<strong>Output:</strong> [48,55,66,77]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= left &lt;= right &lt;= 10<sup>4</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def selfDividingNumbers(self, left: int, right: int) -> List[int]:
        return [
            num
            for num in range(left, right + 1)
            if all(i != '0' and num % int(i) == 0 for i in str(num))
        ]
```

```java
class Solution {
    public List<Integer> selfDividingNumbers(int left, int right) {
        List<Integer> ans = new ArrayList<>();
        for (int i = left; i <= right; ++i) {
            if (check(i)) {
                ans.add(i);
            }
        }
        return ans;
    }

    private boolean check(int num) {
        for (int t = num; t != 0; t /= 10) {
            int x = t % 10;
            if (x == 0 || num % x != 0) {
                return false;
            }
        }
        return true;
    }
}
```

```cpp
class Solution {
public:
    vector<int> selfDividingNumbers(int left, int right) {
        vector<int> ans;
        for (int i = left; i <= right; ++i)
            if (check(i))
                ans.push_back(i);
        return ans;
    }

    bool check(int num) {
        for (int t = num; t; t /= 10) {
            int x = t % 10;
            if (x == 0 || num % x) return false;
        }
        return true;
    }
};
```

```go
func selfDividingNumbers(left int, right int) []int {
	check := func(num int) bool {
		for t := num; t != 0; t /= 10 {
			x := t % 10
			if x == 0 || num%x != 0 {
				return false
			}
		}
		return true
	}

	var ans []int
	for i := left; i <= right; i++ {
		if check(i) {
			ans = append(ans, i)
		}
	}
	return ans
}
```

```rust
impl Solution {
    pub fn self_dividing_numbers(left: i32, right: i32) -> Vec<i32> {
        let mut res = vec![];
        for i in left..=right {
            let mut num = i;
            if (
                loop {
                    if num == 0 {
                        break true;
                    }
                    let j = num % 10;
                    if j == 0 || i % j != 0 {
                        break false;
                    }
                    num /= 10;
                }
            ) {
                res.push(i);
            }
        }
        res
    }
}
```

<!-- tabs:end -->

<!-- end -->
