---
title: 1527 Patients With A Condition
summary: 1527 Patients With A Condition LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "1527 Patients With A Condition LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1527 Patients With A Condition - Solution Explained/problem-solving.webp
    alt: 1527 Patients With A Condition
    hiddenInList: true
    hiddenInSingle: false
---


# [1527. Patients With a Condition](https://leetcode.com/problems/patients-with-a-condition)


## Description

<p>Table: <code>Patients</code></p>

<pre>
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| patient_id   | int     |
| patient_name | varchar |
| conditions   | varchar |
+--------------+---------+
patient_id is the primary key (column with unique values) for this table.
&#39;conditions&#39; contains 0 or more code separated by spaces. 
This table contains information of the patients in the hospital.
</pre>

<p>&nbsp;</p>

<p>Write a solution to find the patient_id, patient_name, and conditions of the patients who have Type I Diabetes. Type I Diabetes always starts with <code>DIAB1</code> prefix.</p>

<p>Return the result table in <strong>any order</strong>.</p>

<p>The&nbsp;result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Patients table:
+------------+--------------+--------------+
| patient_id | patient_name | conditions   |
+------------+--------------+--------------+
| 1          | Daniel       | YFEV COUGH   |
| 2          | Alice        |              |
| 3          | Bob          | DIAB100 MYOP |
| 4          | George       | ACNE DIAB100 |
| 5          | Alain        | DIAB201      |
+------------+--------------+--------------+
<strong>Output:</strong> 
+------------+--------------+--------------+
| patient_id | patient_name | conditions   |
+------------+--------------+--------------+
| 3          | Bob          | DIAB100 MYOP |
| 4          | George       | ACNE DIAB100 | 
+------------+--------------+--------------+
<strong>Explanation:</strong> Bob and George both have a condition that starts with DIAB1.
</pre>

## Solutions

### Solution 1

<!-- tabs:start -->

```sql
SELECT
    patient_id,
    patient_name,
    conditions
FROM patients
WHERE conditions LIKE 'DIAB1%' OR conditions LIKE '% DIAB1%';
```

<!-- tabs:end -->

<!-- end -->
