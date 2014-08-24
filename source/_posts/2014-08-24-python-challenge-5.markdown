---
layout: post
title: "Python Challenge 5"
date: 2014-08-24 15:42:39 +0800
comments: true
categories: [Python,]
---
Challenge 5. [peak hell](http://www.pythonchallenge.com/pc/def/peak.html)

By fininsh loading challenge 5 webpage, it contains one picture and one phrase "pronounce it".

As usual check the source code
``` html
<html>
<head>
  <title>peak hell</title>
  <link rel="stylesheet" type="text/css" href="../style.css">
</head>
<body>
<center>
<img src="peakhell.jpg"/>
<br><font color="#c0c0ff">
pronounce it
<br>
<peakhell src="banner.p"/>
</body>
</html>
<!-- peak hell sounds familiar ? -->
```
Besides the banner.p file founded, the comment "peak hell sounds familiar" bothers me. Just cannot figure out what it means. 
Forget about the comment in html, I just load the file in python to see what inside.
``` python
>>> import urllib2
>>> data = urllib2.urlopen("http://www.pythonchallenge.com/pc/def/banner.p").read()
>>> data
"(lp0\n(lp1\n(S' '\np2\nI95\ntp3\naa(lp4\n(g2\nI14\ntp5\na(S'#'\np6\nI5\ntp7\na(g2\nI70\ntp8\na(g6\nI5\ntp9\na(g2\nI1\ntp10\naa(lp11\n(g2\nI15\ntp12\na(g6\nI4\ntp13\na(g2\nI7
.................
```
It seems like seriers of data, then I try to import pickle package and have a look.
``` python
>>> import pickle
>>> data = pickle.loads(data)
>>> data
[[(' ', 95)], [(' ', 14), ('#', 5), (' ', 70), ('#', 5), (' ', 1)], [(' ', 15), ('#', 4), (' ', 71), ('#', 4), 
.................
```
But it still like a mystery for me.

Beginning of data is ('',95), last is ('',95), second is ('',14) but second last not same, not symmetric. Waite a minute, I find something interesting, inside the dictionary, there are sub dictionaries and inside the sub dict there are tuple(s). The numbers in each sub dictionaries sum together are equal to 95. e.g. the first tuple('',95) obvious is 95. the seconde dictonary contains five tuples ('',14),('#', 5), (' ', 70), ('#', 5), (' ', 1). 14+5+70+5+1=95
Perhaps the 95 is line width, if I printed out maybe will find something.
``` python
>>> for dict in data:
...     for tuple in dict:
...             print tuple[0]*tuple[1]
```
The output remains unknow. Oh, I figure out the problem above code has, I don't have a complete second line.

asdf

``` python
>>> for dict in data:
...     print ''.join(tuple[0] * tuple[1] for tuple in dict)
```
{% img https://dl.dropboxusercontent.com/u/23849021/Blog/Picture/Python/Python%20challenge%205/1.jpg %}

: ) Next challenge is [channel](http://www.pythonchallenge.com/pc/def/channel.html)