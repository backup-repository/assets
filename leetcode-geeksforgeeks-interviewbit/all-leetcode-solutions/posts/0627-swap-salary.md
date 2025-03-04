---
title: 0627 Swap Salary
summary: 0627 Swap Salary LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "0627 Swap Salary LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0627 Swap Salary - Solution Explained/problem-solving.webp
    alt: 0627 Swap Salary
    hiddenInList: true
    hiddenInSingle: false
---


# [627. Swap Salary](https://leetcode.com/problems/swap-salary)


## Description

<p>Table: <code>Salary</code></p>

<pre>
+-------------+----------+
| Column Name | Type     |
+-------------+----------+
| id          | int      |
| name        | varchar  |
| sex         | ENUM     |
| salary      | int      |
+-------------+----------+
id is the primary key (column with unique values) for this table.
The sex column is ENUM (category) value of type (&#39;m&#39;, &#39;f&#39;).
The table contains information about an employee.
</pre>

<p>&nbsp;</p>

<p>Write a solution to swap all <code>&#39;f&#39;</code> and <code>&#39;m&#39;</code> values (i.e., change all <code>&#39;f&#39;</code> values to <code>&#39;m&#39;</code> and vice versa) with a <strong>single update statement</strong> and no intermediate temporary tables.</p>

<p>Note that you must write a single update statement, <strong>do not</strong> write any select statement for this problem.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Salary table:
+----+------+-----+--------+
| id | name | sex | salary |
+----+------+-----+--------+
| 1  | A    | m   | 2500   |
| 2  | B    | f   | 1500   |
| 3  | C    | m   | 5500   |
| 4  | D    | f   | 500    |
+----+------+-----+--------+
<strong>Output:</strong> 
+----+------+-----+--------+
| id | name | sex | salary |
+----+------+-----+--------+
| 1  | A    | f   | 2500   |
| 2  | B    | m   | 1500   |
| 3  | C    | f   | 5500   |
| 4  | D    | m   | 500    |
+----+------+-----+--------+
<strong>Explanation:</strong> 
(1, A) and (3, C) were changed from &#39;m&#39; to &#39;f&#39;.
(2, B) and (4, D) were changed from &#39;f&#39; to &#39;m&#39;.
</pre>

## Solutions

### Solution 1

<!-- tabs:start -->

```sql
UPDATE salary
SET sex = CASE sex
    WHEN 'm' THEN 'f'
    ELSE 'm'
END;
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```sql
# Write your MySQL query statement below
UPDATE Salary
SET sex = IF(sex = 'f', 'm', 'f');
```

<!-- tabs:end -->

<!-- end -->
