---
title: 1079 Letter Tile Possibilities
summary: 1079 Letter Tile Possibilities LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "1079-letter-tile-possibilities LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1079 Letter Tile Possibilities - Solution Explained/problem-solving.webp
    alt: 1079 Letter Tile Possibilities
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/letter-tile-possibilities/">1079. Letter Tile Possibilities</a></h2><h3>Medium</h3><hr><div><p>You have <code>n</code>&nbsp;&nbsp;<code>tiles</code>, where each tile has one letter <code>tiles[i]</code> printed on it.</p>

<p>Return <em>the number of possible non-empty sequences of letters</em> you can make using the letters printed on those <code>tiles</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> tiles = "AAB"
<strong>Output:</strong> 8
<strong>Explanation: </strong>The possible sequences are "A", "B", "AA", "AB", "BA", "AAB", "ABA", "BAA".
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> tiles = "AAABBC"
<strong>Output:</strong> 188
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> tiles = "V"
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= tiles.length &lt;= 7</code></li>
	<li><code>tiles</code> consists of uppercase English letters.</li>
</ul>
</div>

---




```python
# Broute Force
class Solution:
    def numTilePossibilities(self, tiles: str) -> int:
        res = set()
        def dfs(path, tiles):
            if path:
                res.add(path)
            for i in range(len(tiles)):
                dfs(path + tiles[i], tiles[:i] + tiles[i+1:])
        
        dfs("", tiles)
        return len(res)
    
    
# Optimal Solution
class Solution:
    def numTilePossibilities(self, tiles: str) -> int:
        record = [0] * 26
        for tile in tiles: record[ord(tile)-ord('A')] += 1
        def dfs(record):
            s = 0
            for i in range(26):
                if not record[i]: continue
                record[i] -= 1
                s += dfs(record) + 1 
                record[i] += 1
            return s    
        return dfs(record)
```
