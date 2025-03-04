---
title: 0166 Fraction To Recurring Decimal
summary: 0166 Fraction To Recurring Decimal LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "0166 Fraction To Recurring Decimal LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0166 Fraction To Recurring Decimal - Solution Explained/problem-solving.webp
    alt: 0166 Fraction To Recurring Decimal
    hiddenInList: true
    hiddenInSingle: false
---


# [166. Fraction to Recurring Decimal](https://leetcode.com/problems/fraction-to-recurring-decimal)


## Description

<p>Given two integers representing the <code>numerator</code> and <code>denominator</code> of a fraction, return <em>the fraction in string format</em>.</p>

<p>If the fractional part is repeating, enclose the repeating part in parentheses.</p>

<p>If multiple answers are possible, return <strong>any of them</strong>.</p>

<p>It is <strong>guaranteed</strong> that the length of the answer string is less than <code>10<sup>4</sup></code> for all the given inputs.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> numerator = 1, denominator = 2
<strong>Output:</strong> &quot;0.5&quot;
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> numerator = 2, denominator = 1
<strong>Output:</strong> &quot;2&quot;
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> numerator = 4, denominator = 333
<strong>Output:</strong> &quot;0.(012)&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-2<sup>31</sup> &lt;=&nbsp;numerator, denominator &lt;= 2<sup>31</sup> - 1</code></li>
	<li><code>denominator != 0</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def fractionToDecimal(self, numerator: int, denominator: int) -> str:
        if numerator == 0:
            return '0'
        res = []
        neg = (numerator > 0) ^ (denominator > 0)
        if neg:
            res.append('-')
        num, d = abs(numerator), abs(denominator)
        res.append(str(num // d))
        num %= d
        if num == 0:
            return ''.join(res)
        res.append('.')
        mp = {}
        while num != 0:
            mp[num] = len(res)
            num *= 10
            res.append(str(num // d))
            num %= d
            if num in mp:
                idx = mp[num]
                res.insert(idx, '(')
                res.append(')')
                break
        return ''.join(res)
```

```java
class Solution {
    public String fractionToDecimal(int numerator, int denominator) {
        if (numerator == 0) {
            return "0";
        }
        StringBuilder sb = new StringBuilder();
        boolean neg = (numerator > 0) ^ (denominator > 0);
        sb.append(neg ? "-" : "");
        long num = Math.abs((long) numerator);
        long d = Math.abs((long) denominator);
        sb.append(num / d);
        num %= d;
        if (num == 0) {
            return sb.toString();
        }
        sb.append(".");
        Map<Long, Integer> mp = new HashMap<>();
        while (num != 0) {
            mp.put(num, sb.length());
            num *= 10;
            sb.append(num / d);
            num %= d;
            if (mp.containsKey(num)) {
                int idx = mp.get(num);
                sb.insert(idx, "(");
                sb.append(")");
                break;
            }
        }
        return sb.toString();
    }
}
```

```cpp
using LL = long long;

class Solution {
public:
    string fractionToDecimal(int numerator, int denominator) {
        if (numerator == 0) return "0";
        string res = "";
        bool neg = (numerator > 0) ^ (denominator > 0);
        if (neg) res += "-";
        LL num = abs(numerator);
        LL d = abs(denominator);
        res += to_string(num / d);
        num %= d;
        if (num == 0) return res;
        res += ".";
        unordered_map<LL, int> mp;
        while (num) {
            mp[num] = res.size();
            num *= 10;
            res += to_string(num / d);
            num %= d;
            if (mp.count(num)) {
                int idx = mp[num];
                res.insert(idx, "(");
                res += ")";
                break;
            }
        }
        return res;
    }
};
```

```go
func fractionToDecimal(numerator int, denominator int) string {
	if numerator == 0 {
		return "0"
	}
	res := []byte{}
	neg := numerator*denominator < 0
	if neg {
		res = append(res, '-')
	}
	num := abs(numerator)
	d := abs(denominator)
	res = append(res, strconv.Itoa(num/d)...)
	num %= d
	if num == 0 {
		return string(res)
	}
	mp := make(map[int]int)
	res = append(res, '.')
	for num != 0 {
		mp[num] = len(res)
		num *= 10
		res = append(res, strconv.Itoa(num/d)...)
		num %= d
		if mp[num] > 0 {
			idx := mp[num]
			res = append(res[:idx], append([]byte{'('}, res[idx:]...)...)
			res = append(res, ')')
			break
		}
	}

	return string(res)
}

func abs(x int) int {
	if x < 0 {
		return -x
	}
	return x
}
```

```cs
﻿// https://leetcode.com/problems/fraction-to-recurring-decimal/

using System.Collections.Generic;
using System.Text;

public partial class Solution
{
    public string FractionToDecimal(int numerator, int denominator)
    {
        var n = (long)numerator;
        var d = (long)denominator;
        var sb = new StringBuilder();
        if (n < 0)
        {
            n = -n;
            if (d < 0)
            {
                d = -d;
            }
            else
            {
                sb.Append('-');
            }
        }
        else if (n > 0 && d < 0)
        {
            d = -d;
            sb.Append('-');
        }

        sb.Append(n / d);
        n = n % d;
        if (n != 0)
        {
            sb.Append('.');
            var dict = new Dictionary<long, int>();
            while (n != 0)
            {
                int index;
                if (dict.TryGetValue(n, out index))
                {
                    sb.Insert(index, '(');
                    sb.Append(')');
                    break;
                }
                else
                {
                    dict.Add(n, sb.Length);
                    n *= 10;
                    sb.Append(n / d);
                    n %= d;
                }
            }
        }
        return sb.ToString();
    }
}
```

<!-- tabs:end -->

<!-- end -->
