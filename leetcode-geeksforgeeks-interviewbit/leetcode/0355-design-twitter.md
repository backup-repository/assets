---
title: 0355 Design Twitter
summary: 0355 Design Twitter LeetCode Solution Explained
date: 2020-06-20
tags: [leetcode]
series: [leetcode]
keywords: ["LeetCode", "leetcode solution in Python3 C++ Java", "0355-design-twitter LeetCode Solution Explained"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0355 Design Twitter - Solution Explained/problem-solving.webp
    alt: 0355 Design Twitter
    hiddenInList: true
    hiddenInSingle: false
---


<h2><a href="https://leetcode.com/problems/design-twitter/">355. Design Twitter</a></h2><h3>Medium</h3><hr><div><p>Design a simplified version of Twitter where users can post tweets, follow/unfollow another user, and is able to see the <code>10</code> most recent tweets in the user's news feed.</p>

<p>Implement the <code>Twitter</code> class:</p>

<ul>
	<li><code>Twitter()</code> Initializes your twitter object.</li>
	<li><code>void postTweet(int userId, int tweetId)</code> Composes a new tweet with ID <code>tweetId</code> by the user <code>userId</code>. Each call to this function will be made with a unique <code>tweetId</code>.</li>
	<li><code>List&lt;Integer&gt; getNewsFeed(int userId)</code> Retrieves the <code>10</code> most recent tweet IDs in the user's news feed. Each item in the news feed must be posted by users who the user followed or by the user themself. Tweets must be <strong>ordered from most recent to least recent</strong>.</li>
	<li><code>void follow(int followerId, int followeeId)</code> The user with ID <code>followerId</code> started following the user with ID <code>followeeId</code>.</li>
	<li><code>void unfollow(int followerId, int followeeId)</code> The user with ID <code>followerId</code> started unfollowing the user with ID <code>followeeId</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input</strong>
["Twitter", "postTweet", "getNewsFeed", "follow", "postTweet", "getNewsFeed", "unfollow", "getNewsFeed"]
[[], [1, 5], [1], [1, 2], [2, 6], [1], [1, 2], [1]]
<strong>Output</strong>
[null, null, [5], null, null, [6, 5], null, [5]]

<strong>Explanation</strong>
Twitter twitter = new Twitter();
twitter.postTweet(1, 5); // User 1 posts a new tweet (id = 5).
twitter.getNewsFeed(1);  // User 1's news feed should return a list with 1 tweet id -&gt; [5]. return [5]
twitter.follow(1, 2);    // User 1 follows user 2.
twitter.postTweet(2, 6); // User 2 posts a new tweet (id = 6).
twitter.getNewsFeed(1);  // User 1's news feed should return a list with 2 tweet ids -&gt; [6, 5]. Tweet id 6 should precede tweet id 5 because it is posted after tweet id 5.
twitter.unfollow(1, 2);  // User 1 unfollows user 2.
twitter.getNewsFeed(1);  // User 1's news feed should return a list with 1 tweet id -&gt; [5], since user 1 is no longer following user 2.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= userId, followerId, followeeId &lt;= 500</code></li>
	<li><code>0 &lt;= tweetId &lt;= 10<sup>4</sup></code></li>
	<li>All the tweets have <strong>unique</strong> IDs.</li>
	<li>At most <code>3 * 10<sup>4</sup></code> calls will be made to <code>postTweet</code>, <code>getNewsFeed</code>, <code>follow</code>, and <code>unfollow</code>.</li>
</ul>
</div>

---




```python
class Twitter:

    def __init__(self):
        self.tweets = []
        self.following = collections.defaultdict(set)

    def postTweet(self, userId: int, tweetId: int) -> None:
        self.tweets.append((userId, tweetId))

    def getNewsFeed(self, userId: int) -> List[int]:
        res = []
        i = len(self.tweets)-1
        while i >= 0 and len(res) < 10:
            u, t = self.tweets[i]
            if u == userId or u in self.following[userId]:
                res.append(t)
            i -= 1
        return res

    def follow(self, followerId: int, followeeId: int) -> None:
        self.following[followerId].add(followeeId)

    def unfollow(self, followerId: int, followeeId: int) -> None:
        if followeeId in self.following[followerId]:
            self.following[followerId].remove(followeeId)
```
