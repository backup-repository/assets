---
title: 2890 Reshape Data Melt
summary: 2890 Reshape Data Melt LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "2890 Reshape Data Melt LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2890 Reshape Data Melt - Solution Explained/problem-solving.webp
    alt: 2890 Reshape Data Melt
    hiddenInList: true
    hiddenInSingle: false
---


# [2890. Reshape Data Melt](https://leetcode.com/problems/reshape-data-melt)


## Description

<pre>
DataFrame <code>report</code>
+-------------+--------+
| Column Name | Type   |
+-------------+--------+
| product     | object |
| quarter_1   | int    |
| quarter_2   | int    |
| quarter_3   | int    |
| quarter_4   | int    |
+-------------+--------+
</pre>

<p>Write a solution to <strong>reshape</strong> the data so that each row represents sales data for a product in a specific quarter.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:
</strong>+-------------+-----------+-----------+-----------+-----------+
| product     | quarter_1 | quarter_2 | quarter_3 | quarter_4 |
+-------------+-----------+-----------+-----------+-----------+
| Umbrella    | 417       | 224       | 379       | 611       |
| SleepingBag | 800       | 936       | 93        | 875       |
+-------------+-----------+-----------+-----------+-----------+
<strong>Output:</strong>
+-------------+-----------+-------+
| product     | quarter   | sales |
+-------------+-----------+-------+
| Umbrella    | quarter_1 | 417   |
| SleepingBag | quarter_1 | 800   |
| Umbrella    | quarter_2 | 224   |
| SleepingBag | quarter_2 | 936   |
| Umbrella    | quarter_3 | 379   |
| SleepingBag | quarter_3 | 93    |
| Umbrella    | quarter_4 | 611   |
| SleepingBag | quarter_4 | 875   |
+-------------+-----------+-------+
<strong>Explanation:</strong>
The DataFrame is reshaped from wide to long format. Each row represents the sales of a product in a quarter.
</pre>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
import pandas as pd


def meltTable(report: pd.DataFrame) -> pd.DataFrame:
    return pd.melt(report, id_vars=['product'], var_name='quarter', value_name='sales')
```

<!-- tabs:end -->

<!-- end -->
