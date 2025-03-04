---
title: 2194 Cells In A Range On An Excel Sheet
summary: 2194 Cells In A Range On An Excel Sheet LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "2194 Cells In A Range On An Excel Sheet LeetCode Solution Explained in all languages"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2194 Cells In A Range On An Excel Sheet - Solution Explained/problem-solving.webp
    alt: 2194 Cells In A Range On An Excel Sheet
    hiddenInList: true
    hiddenInSingle: false
---


# [2194. Cells in a Range on an Excel Sheet](https://leetcode.com/problems/cells-in-a-range-on-an-excel-sheet)


## Description

<p>A cell <code>(r, c)</code> of an excel sheet is represented as a string <code>&quot;&lt;col&gt;&lt;row&gt;&quot;</code> where:</p>

<ul>
	<li><code>&lt;col&gt;</code> denotes the column number <code>c</code> of the cell. It is represented by <strong>alphabetical letters</strong>.

    <ul>
    	<li>For example, the <code>1<sup>st</sup></code> column is denoted by <code>&#39;A&#39;</code>, the <code>2<sup>nd</sup></code> by <code>&#39;B&#39;</code>, the <code>3<sup>rd</sup></code> by <code>&#39;C&#39;</code>, and so on.</li>
    </ul>
    </li>
    <li><code>&lt;row&gt;</code> is the row number <code>r</code> of the cell. The <code>r<sup>th</sup></code> row is represented by the <strong>integer</strong> <code>r</code>.</li>

</ul>

<p>You are given a string <code>s</code>&nbsp;in&nbsp;the format <code>&quot;&lt;col1&gt;&lt;row1&gt;:&lt;col2&gt;&lt;row2&gt;&quot;</code>, where <code>&lt;col1&gt;</code> represents the column <code>c1</code>, <code>&lt;row1&gt;</code> represents the row <code>r1</code>, <code>&lt;col2&gt;</code> represents the column <code>c2</code>, and <code>&lt;row2&gt;</code> represents the row <code>r2</code>, such that <code>r1 &lt;= r2</code> and <code>c1 &lt;= c2</code>.</p>

<p>Return <em>the <strong>list of cells</strong></em> <code>(x, y)</code> <em>such that</em> <code>r1 &lt;= x &lt;= r2</code> <em>and</em> <code>c1 &lt;= y &lt;= c2</code>. The cells should be represented as&nbsp;<strong>strings</strong> in the format mentioned above and be sorted in <strong>non-decreasing</strong> order first by columns and then by rows.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/solution/2100-2199/2194.Cells%20in%20a%20Range%20on%20an%20Excel%20Sheet/images/ex1drawio.png" style="width: 250px; height: 160px;" />
<pre>
<strong>Input:</strong> s = &quot;K1:L2&quot;
<strong>Output:</strong> [&quot;K1&quot;,&quot;K2&quot;,&quot;L1&quot;,&quot;L2&quot;]
<strong>Explanation:</strong>
The above diagram shows the cells which should be present in the list.
The red arrows denote the order in which the cells should be presented.
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/solution/2100-2199/2194.Cells%20in%20a%20Range%20on%20an%20Excel%20Sheet/images/exam2drawio.png" style="width: 500px; height: 50px;" />
<pre>
<strong>Input:</strong> s = &quot;A1:F1&quot;
<strong>Output:</strong> [&quot;A1&quot;,&quot;B1&quot;,&quot;C1&quot;,&quot;D1&quot;,&quot;E1&quot;,&quot;F1&quot;]
<strong>Explanation:</strong>
The above diagram shows the cells which should be present in the list.
The red arrow denotes the order in which the cells should be presented.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>s.length == 5</code></li>
	<li><code>&#39;A&#39; &lt;= s[0] &lt;= s[3] &lt;= &#39;Z&#39;</code></li>
	<li><code>&#39;1&#39; &lt;= s[1] &lt;= s[4] &lt;= &#39;9&#39;</code></li>
	<li><code>s</code> consists of uppercase English letters, digits and <code>&#39;:&#39;</code>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def cellsInRange(self, s: str) -> List[str]:
        return [
            chr(i) + str(j)
            for i in range(ord(s[0]), ord(s[-2]) + 1)
            for j in range(int(s[1]), int(s[-1]) + 1)
        ]
```

```java
class Solution {
    public List<String> cellsInRange(String s) {
        List<String> ans = new ArrayList<>();
        for (char i = s.charAt(0); i <= s.charAt(3); ++i) {
            for (char j = s.charAt(1); j <= s.charAt(4); ++j) {
                ans.add(i + "" + j);
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    vector<string> cellsInRange(string s) {
        vector<string> ans;
        for (char i = s[0]; i <= s[3]; ++i)
            for (char j = s[1]; j <= s[4]; ++j)
                ans.push_back({i, j});
        return ans;
    }
};
```

```go
func cellsInRange(s string) []string {
	var ans []string
	for i := s[0]; i <= s[3]; i++ {
		for j := s[1]; j <= s[4]; j++ {
			ans = append(ans, string(i)+string(j))
		}
	}
	return ans
}
```

<!-- tabs:end -->

<!-- end -->
