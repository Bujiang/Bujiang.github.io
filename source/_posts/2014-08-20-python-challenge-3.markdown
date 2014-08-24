---
layout: post
title: "Python challenge 3"
date: 2014-08-20 00:10:44 +0800
comments: true
categories: [Python,]
---
Challenge 3. [re](http://www.pythonchallenge.com/pc/def/equality.html)

Like previous challenge, this challenge contains one picture and one pargraph.
{% blockquote %}
One small letter, surrounded by EXACTLY three big bodyguards on each of its sides.
{% endblockquote %}

The title of challenge 3 page is re, maybe this is another hint telling me to use re package?
``` python
>>> import urllib2
>>> data = urllib2.urlopen("http://www.pythonchallenge.com/pc/def/equality.html")
>>> data = data.read()
>>> print "".join(re.findall("[^A-Z][A-Z]{3}([a-z])[A-Z]{3}[^A-Z]", data))
linkedlist
```

[^A-Z] matches any single character not in it

[A-Z]{3} matches three UPPERCASE characters

Next challenge is [linkedlist](http://www.pythonchallenge.com/pc/def/linkedlist.html)