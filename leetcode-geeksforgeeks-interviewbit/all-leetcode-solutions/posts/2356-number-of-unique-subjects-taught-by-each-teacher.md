---
title: 2356 Number Of Unique Subjects Taught By Each Teacher
summary: 2356 Number Of Unique Subjects Taught By Each Teacher LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "2356 Number Of Unique Subjects Taught By Each Teacher LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2356 Number Of Unique Subjects Taught By Each Teacher - Solution Explained/problem-solving.webp
    alt: 2356 Number Of Unique Subjects Taught By Each Teacher
    hiddenInList: true
    hiddenInSingle: false
---


# [2356. Number of Unique Subjects Taught by Each Teacher](https://leetcode.com/problems/number-of-unique-subjects-taught-by-each-teacher)


## Description

<p>Table: <code>Teacher</code></p>

<pre>
+-------------+------+
| Column Name | Type |
+-------------+------+
| teacher_id  | int  |
| subject_id  | int  |
| dept_id     | int  |
+-------------+------+
(subject_id, dept_id) is the primary key (combinations of columns with unique values) of this table.
Each row in this table indicates that the teacher with teacher_id teaches the subject subject_id in the department dept_id.
</pre>

<p>&nbsp;</p>

<p>Write a solution to calculate&nbsp;the number of unique subjects each teacher teaches in the university.</p>

<p>Return the result table in <strong>any order</strong>.</p>

<p>The&nbsp;result format is shown in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Teacher table:
+------------+------------+---------+
| teacher_id | subject_id | dept_id |
+------------+------------+---------+
| 1          | 2          | 3       |
| 1          | 2          | 4       |
| 1          | 3          | 3       |
| 2          | 1          | 1       |
| 2          | 2          | 1       |
| 2          | 3          | 1       |
| 2          | 4          | 1       |
+------------+------------+---------+
<strong>Output:</strong>  
+------------+-----+
| teacher_id | cnt |
+------------+-----+
| 1          | 2   |
| 2          | 4   |
+------------+-----+
<strong>Explanation:</strong> 
Teacher 1:
  - They teach subject 2 in departments 3 and 4.
  - They teach subject 3 in department 3.
Teacher 2:
  - They teach subject 1 in department 1.
  - They teach subject 2 in department 1.
  - They teach subject 3 in department 1.
  - They teach subject 4 in department 1.
</pre>

## Solutions

### Solution 1

<!-- tabs:start -->

```sql
# Write your MySQL query statement below
SELECT teacher_id, COUNT(DISTINCT subject_id) AS cnt
FROM Teacher
GROUP BY 1;
```

<!-- tabs:end -->

<!-- end -->
