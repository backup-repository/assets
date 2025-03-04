---
title: Rabbits In Forest
summary: Rabbits In Forest LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "rabbits-in-forest LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Rabbits In Forest - Solution Explained/problem-solving.webp
    alt: Rabbits In Forest
    hiddenInList: true
    hiddenInSingle: false
---


<h2>781. Rabbits in Forest</h2><h3>Medium</h3><hr><div><p>In a forest, each rabbit has some color. Some subset of rabbits (possibly all of them) tell you how many other rabbits have the same color as them. Those <code>answers</code> are placed in an array.</p>

<p>Return the minimum number of rabbits that could be in the forest.</p>

<pre><strong>Examples:</strong>
<strong>Input:</strong> answers = [1, 1, 2]
<strong>Output:</strong> 5
<strong>Explanation:</strong>
The two rabbits that answered "1" could both be the same color, say red.
The rabbit than answered "2" can't be red or the answers would be inconsistent.
Say the rabbit that answered "2" was blue.
Then there should be 2 other blue rabbits in the forest that didn't answer into the array.
The smallest possible number of rabbits in the forest is therefore 5: 3 that answered plus 2 that didn't.

<strong>Input:</strong> answers = [10, 10, 10]
<strong>Output:</strong> 11

<strong>Input:</strong> answers = []
<strong>Output:</strong> 0
</pre>

<p><strong>Note:</strong></p>

<ol>
	<li><code>answers</code> will have length at most <code>1000</code>.</li>
	<li>Each <code>answers[i]</code> will be an integer in the range <code>[0, 999]</code>.</li>
</ol>
</div>

---




```cpp
class Solution {
public:
    int numRabbits(vector<int>& answers) {
        int n=answers.size();
        map<int,int> m;
        int ans=0;
        for(int i=0;i<n;i++)
            m[answers[i]]++;
        map<int,int>::iterator it;
        for(it=m.begin();it!=m.end();it++){
            int x=it->first+1;
            int y=it->second;
            int t=y%x;
            if(t>0)
                ans+=y-t+x;
            else
                ans+=y;
        }
        return ans;
    }
};
```
