---
title: 0602 Friend Requests Ii Who Has The Most Friends
summary: 0602 Friend Requests Ii Who Has The Most Friends LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "0602 Friend Requests Ii Who Has The Most Friends LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0602 Friend Requests Ii Who Has The Most Friends - Solution Explained/problem-solving.webp
    alt: 0602 Friend Requests Ii Who Has The Most Friends
    hiddenInList: true
    hiddenInSingle: false
---


# [602. Friend Requests II Who Has the Most Friends](https://leetcode.com/problems/friend-requests-ii-who-has-the-most-friends)


## Description

<p>Table: <code>RequestAccepted</code></p>

<pre>
+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| requester_id   | int     |
| accepter_id    | int     |
| accept_date    | date    |
+----------------+---------+
(requester_id, accepter_id) is the primary key (combination of columns with unique values) for this table.
This table contains the ID of the user who sent the request, the ID of the user who received the request, and the date when the request was accepted.
</pre>

<p>&nbsp;</p>

<p>Write a solution to find the people who have the most friends and the most friends number.</p>

<p>The test cases are generated so that only one person has the most friends.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
RequestAccepted table:
+--------------+-------------+-------------+
| requester_id | accepter_id | accept_date |
+--------------+-------------+-------------+
| 1            | 2           | 2016/06/03  |
| 1            | 3           | 2016/06/08  |
| 2            | 3           | 2016/06/08  |
| 3            | 4           | 2016/06/09  |
+--------------+-------------+-------------+
<strong>Output:</strong> 
+----+-----+
| id | num |
+----+-----+
| 3  | 3   |
+----+-----+
<strong>Explanation:</strong> 
The person with id 3 is a friend of people 1, 2, and 4, so he has three friends in total, which is the most number than any others.
</pre>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> In the real world, multiple people could have the same most number of friends. Could you find all these people in this case?</p>

## Solutions

### Solution 1

<!-- tabs:start -->

```sql
# Write your MySQL query statement below
WITH
    T AS (
        SELECT requester_id, accepter_id FROM RequestAccepted
        UNION
        SELECT accepter_id, requester_id FROM RequestAccepted
    )
SELECT requester_id AS id, COUNT(accepter_id) AS num
FROM T
GROUP BY 1
ORDER BY 2 DESC
LIMIT 1;
```

<!-- tabs:end -->

<!-- end -->
