---
title: 71 Simplify Path
summary: 71 Simplify Path LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "71-simplify-path LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:71 Simplify Path - Solution Explained/problem-solving.webp
    alt: 71 Simplify Path
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/simplify-path/">71. Simplify Path</a></h2><h3>Medium</h3><hr><div><p>Given a string <code>path</code>, which is an <strong>absolute path</strong> (starting with a slash <code>'/'</code>) to a file or directory in a Unix-style file system, convert it to the simplified <strong>canonical path</strong>.</p>

<p>In a Unix-style file system, a period <code>'.'</code> refers to the current directory, a double period <code>'..'</code> refers to the directory up a level, and any multiple consecutive slashes (i.e. <code>'//'</code>) are treated as a single slash <code>'/'</code>. For this problem, any other format of periods such as <code>'...'</code> are treated as file/directory names.</p>

<p>The <strong>canonical path</strong> should have the following format:</p>

<ul>
	<li>The path starts with a single slash <code>'/'</code>.</li>
	<li>Any two directories are separated by a single slash <code>'/'</code>.</li>
	<li>The path does not end with a trailing <code>'/'</code>.</li>
	<li>The path only contains the directories on the path from the root directory to the target file or directory (i.e., no period <code>'.'</code> or double period <code>'..'</code>)</li>
</ul>

<p>Return <em>the simplified <strong>canonical path</strong></em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> path = "/home/"
<strong>Output:</strong> "/home"
<strong>Explanation:</strong> Note that there is no trailing slash after the last directory name.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> path = "/../"
<strong>Output:</strong> "/"
<strong>Explanation:</strong> Going one level up from the root directory is a no-op, as the root level is the highest level you can go.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> path = "/home//foo/"
<strong>Output:</strong> "/home/foo"
<strong>Explanation:</strong> In the canonical path, multiple consecutive slashes are replaced by a single one.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= path.length &lt;= 3000</code></li>
	<li><code>path</code> consists of English letters, digits, period <code>'.'</code>, slash <code>'/'</code> or <code>'_'</code>.</li>
	<li><code>path</code> is a valid absolute Unix path.</li>
</ul>
</div>

---




```python
class Solution:
    def simplifyPath(self, path: str) -> str:
        stack = []
        i = 0
        while i < len(path):
            cur = path[i]
            i += 1
            if cur == '/':
                while i < len(path) and path[i] == '/':
                    cur += path[i]
                    i += 1
            else:
                while i < len(path) and path[i] != '/':
                    cur += path[i]
                    i += 1
                    
            if cur == '..': 
                if stack: stack.pop()
            elif cur[0] != '/' and cur != '.': 
                stack.append(cur)
        
        res = ''
        for s in stack: res += '/' + s
            
        return res if res else '/'

    
    
    
'''Test Cases:

"/home/"
"/../"
"/home//foo/"
"/a/./b/../../c/"
"/a//b////c/d//././/.."
"/..."
"/..hidden"
"/a/../../b/../c//.//"
'''
```
