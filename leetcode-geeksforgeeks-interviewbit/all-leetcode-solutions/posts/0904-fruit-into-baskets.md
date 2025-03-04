---
title: 0904 Fruit Into Baskets
summary: 0904 Fruit Into Baskets LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "0904 Fruit Into Baskets LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0904 Fruit Into Baskets - Solution Explained/problem-solving.webp
    alt: 0904 Fruit Into Baskets
    hiddenInList: true
    hiddenInSingle: false
---


# [904. Fruit Into Baskets](https://leetcode.com/problems/fruit-into-baskets)


## Description

<p>You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array <code>fruits</code> where <code>fruits[i]</code> is the <strong>type</strong> of fruit the <code>i<sup>th</sup></code> tree produces.</p>

<p>You want to collect as much fruit as possible. However, the owner has some strict rules that you must follow:</p>

<ul>
	<li>You only have <strong>two</strong> baskets, and each basket can only hold a <strong>single type</strong> of fruit. There is no limit on the amount of fruit each basket can hold.</li>
	<li>Starting from any tree of your choice, you must pick <strong>exactly one fruit</strong> from <strong>every</strong> tree (including the start tree) while moving to the right. The picked fruits must fit in one of your baskets.</li>
	<li>Once you reach a tree with fruit that cannot fit in your baskets, you must stop.</li>
</ul>

<p>Given the integer array <code>fruits</code>, return <em>the <strong>maximum</strong> number of fruits you can pick</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> fruits = [<u>1,2,1</u>]
<strong>Output:</strong> 3
<strong>Explanation:</strong> We can pick from all 3 trees.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> fruits = [0,<u>1,2,2</u>]
<strong>Output:</strong> 3
<strong>Explanation:</strong> We can pick from trees [1,2,2].
If we had started at the first tree, we would only pick from trees [0,1].
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> fruits = [1,<u>2,3,2,2</u>]
<strong>Output:</strong> 4
<strong>Explanation:</strong> We can pick from trees [2,3,2,2].
If we had started at the first tree, we would only pick from trees [1,2].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= fruits.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= fruits[i] &lt; fruits.length</code></li>
</ul>

## Solutions

### Solution 1: Hash Table + Sliding Window

We use a hash table $cnt$ to maintain the types and corresponding quantities of fruits in the current window, and use two pointers $j$ and $i$ to maintain the left and right boundaries of the window.

We traverse the `fruits` array, add the current fruit $x$ to the window, i.e., $cnt[x]++$, then judge whether the types of fruits in the current window exceed $2$. If it exceeds $2$, we need to move the left boundary $j$ of the window to the right until the types of fruits in the window do not exceed $2$. Then we update the answer, i.e., $ans = \max(ans, i - j + 1)$.

After the traversal ends, we can get the final answer.

```
1 2 3 2 2 1 4
^   ^
j   i


1 2 3 2 2 1 4
  ^ ^
  j i


1 2 3 2 2 1 4
  ^     ^
  j     i
```

The time complexity is $O(n)$, and the space complexity is $O(1)$. Here, $n$ is the length of the `fruits` array.

<!-- tabs:start -->

```python
class Solution:
    def totalFruit(self, fruits: List[int]) -> int:
        cnt = Counter()
        ans = j = 0
        for i, x in enumerate(fruits):
            cnt[x] += 1
            while len(cnt) > 2:
                y = fruits[j]
                cnt[y] -= 1
                if cnt[y] == 0:
                    cnt.pop(y)
                j += 1
            ans = max(ans, i - j + 1)
        return ans
```

```java
class Solution {
    public int totalFruit(int[] fruits) {
        Map<Integer, Integer> cnt = new HashMap<>();
        int ans = 0;
        for (int i = 0, j = 0; i < fruits.length; ++i) {
            int x = fruits[i];
            cnt.put(x, cnt.getOrDefault(x, 0) + 1);
            while (cnt.size() > 2) {
                int y = fruits[j++];
                cnt.put(y, cnt.get(y) - 1);
                if (cnt.get(y) == 0) {
                    cnt.remove(y);
                }
            }
            ans = Math.max(ans, i - j + 1);
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int totalFruit(vector<int>& fruits) {
        unordered_map<int, int> cnt;
        int ans = 0;
        for (int i = 0, j = 0; i < fruits.size(); ++i) {
            int x = fruits[i];
            ++cnt[x];
            while (cnt.size() > 2) {
                int y = fruits[j++];
                if (--cnt[y] == 0) cnt.erase(y);
            }
            ans = max(ans, i - j + 1);
        }
        return ans;
    }
};
```

```go
func totalFruit(fruits []int) int {
	cnt := map[int]int{}
	ans, j := 0, 0
	for i, x := range fruits {
		cnt[x]++
		for ; len(cnt) > 2; j++ {
			y := fruits[j]
			cnt[y]--
			if cnt[y] == 0 {
				delete(cnt, y)
			}
		}
		ans = max(ans, i-j+1)
	}
	return ans
}
```

```ts
function totalFruit(fruits: number[]): number {
    const n = fruits.length;
    const map = new Map<number, number>();
    let res = 0;
    let left = 0;
    let right = 0;
    while (right < n) {
        map.set(fruits[right], (map.get(fruits[right]) ?? 0) + 1);
        right++;
        while (map.size > 2) {
            const k = fruits[left++];
            map.set(k, map.get(k) - 1);
            if (map.get(k) === 0) {
                map.delete(k);
            }
        }
        res = Math.max(res, right - left);
    }
    return res;
}
```

```rust
use std::collections::HashMap;
impl Solution {
    pub fn total_fruit(fruits: Vec<i32>) -> i32 {
        let n = fruits.len();
        let mut map = HashMap::new();
        let mut res = 0;
        let mut left = 0;
        let mut right = 0;
        while right < n {
            *map.entry(fruits[right]).or_insert(0) += 1;
            right += 1;
            while map.len() > 2 {
                let k = fruits[left];
                map.insert(k, map[&k] - 1);
                if map[&k] == 0 {
                    map.remove(&k);
                }
                left += 1;
            }
            res = res.max(right - left);
        }
        res as i32
    }
}
```

<!-- tabs:end -->

### Solution 2: Sliding Window Optimization

In Solution 1, we find that the window size sometimes increases and sometimes decreases, which requires us to update the answer each time.

But what this problem actually asks for is the maximum number of fruits, that is, the "largest" window. We don't need to shrink the window, we just need to let the window monotonically increase. So the code omits the operation of updating the answer each time, and only needs to return the size of the window as the answer after the traversal ends.

The time complexity is $O(n)$, and the space complexity is $O(1)$. Here, $n$ is the length of the `fruits` array.

<!-- tabs:start -->

```python
class Solution:
    def totalFruit(self, fruits: List[int]) -> int:
        cnt = Counter()
        j = 0
        for x in fruits:
            cnt[x] += 1
            if len(cnt) > 2:
                y = fruits[j]
                cnt[y] -= 1
                if cnt[y] == 0:
                    cnt.pop(y)
                j += 1
        return len(fruits) - j
```

```java
class Solution {
    public int totalFruit(int[] fruits) {
        Map<Integer, Integer> cnt = new HashMap<>();
        int j = 0, n = fruits.length;
        for (int x : fruits) {
            cnt.put(x, cnt.getOrDefault(x, 0) + 1);
            if (cnt.size() > 2) {
                int y = fruits[j++];
                cnt.put(y, cnt.get(y) - 1);
                if (cnt.get(y) == 0) {
                    cnt.remove(y);
                }
            }
        }
        return n - j;
    }
}
```

```cpp
class Solution {
public:
    int totalFruit(vector<int>& fruits) {
        unordered_map<int, int> cnt;
        int j = 0, n = fruits.size();
        for (int& x : fruits) {
            ++cnt[x];
            if (cnt.size() > 2) {
                int y = fruits[j++];
                if (--cnt[y] == 0) cnt.erase(y);
            }
        }
        return n - j;
    }
};
```

```go
func totalFruit(fruits []int) int {
	cnt := map[int]int{}
	j := 0
	for _, x := range fruits {
		cnt[x]++
		if len(cnt) > 2 {
			y := fruits[j]
			cnt[y]--
			if cnt[y] == 0 {
				delete(cnt, y)
			}
			j++
		}
	}
	return len(fruits) - j
}
```

```ts
function totalFruit(fruits: number[]): number {
    const n = fruits.length;
    const map = new Map<number, number>();
    let i = 0;
    for (const fruit of fruits) {
        map.set(fruit, (map.get(fruit) ?? 0) + 1);
        if (map.size > 2) {
            const k = fruits[i++];
            map.set(k, map.get(k) - 1);
            if (map.get(k) == 0) {
                map.delete(k);
            }
        }
    }
    return n - i;
}
```

```rust
use std::collections::HashMap;
impl Solution {
    pub fn total_fruit(fruits: Vec<i32>) -> i32 {
        let n = fruits.len();
        let mut map = HashMap::new();
        let mut i = 0;
        for &fruit in fruits.iter() {
            *map.entry(fruit).or_insert(0) += 1;
            if map.len() > 2 {
                let k = fruits[i];
                map.insert(k, map[&k] - 1);
                if map[&k] == 0 {
                    map.remove(&k);
                }
                i += 1;
            }
        }
        (n - i) as i32
    }
}
```

<!-- tabs:end -->

<!-- end -->
