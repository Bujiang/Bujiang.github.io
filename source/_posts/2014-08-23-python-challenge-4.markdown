---
layout: post
title: "Python challenge 4"
date: 2014-08-23 12:58:39 +0800
comments: true
categories: [Python,]
---
Challenge 4. [linkedlist](http://www.pythonchallenge.com/pc/def/linkedlist.html)

Open the resolved url in browser, it shows linkedlist.php. 

Finish loading [http://www.pythonchallenge.com/pc/def/linkedlist.php](http://www.pythonchallenge.com/pc/def/linkedlist.php) there only lefe one picture. 
As before, I check the page source code and find a new link [http://www.pythonchallenge.com/pc/def/linkedlist.php?nothing=12345](http://www.pythonchallenge.com/pc/def/linkedlist.php?nothing=12345). I just try open the new url, and the page dispaly "and the next nothing is 44827". 
It seems need me to automate recursive open url by using python.

``` python
import urllib2, re

url = "http://www.pythonchallenge.com/pc/def/linkedlist.php?nothing="
nothingValue = "12345"
digis = "\d+"

data = urllib2.urlopen(url + nothingValue).read()
print data
finding = re.search(digis, data)

while finding.group(0):
    nothingValue = finding.group(0)
    data = urllib2.urlopen(url + nothingValue).read()
    print data
    finding = re.search(digis, data)

print data
```

Above code will find the digitals in webpage and use the finding digitals to do a new request.

``` bash
.............
and the next nothing is 29247
and the next nothing is 13115
and the next nothing is 23053
and the next nothing is 3875
and the next nothing is 16044
Yes. Divide by two and keep going.
Traceback (most recent call last):
  File "bu.py", line 11, in <module>
    while finding.group(0):
AttributeError: 'NoneType' object has no attribute 'group'
```
After run a while, the last printed line shows none digitals "Divide by two and keep going" By divide 16044 with 2 get 8022, then modify nothingValue in script then continue run.
``` bash
..............
and the next nothing is 49574
and the next nothing is 82682
There maybe misleading numbers in the 
text. One example is 82683. Look only for the next nothing and the next nothing is 63579
You've been misleaded to here. Go to previous 
one and check.
Traceback (most recent call last):
  File "bu.py", line 11, in <module>
    while finding.group(0):
AttributeError: 'NoneType' object has no attribute 'group'
```
But still got some problem here, it tells "One example is 82683...." I've search print statement history but can't find it.
I continue modify the nothingValue to 63579 and re-run again.
``` bash
and the next nothing is 27709
and the next nothing is 96791
and the next nothing is 75635
and the next nothing is 52899
and the next nothing is 66831
peak.html
Traceback (most recent call last):
  File "bu.py", line 11, in <module>
    while finding.group(0):
AttributeError: 'NoneType' object has no attribute 'group'
``` 
It seems OK here. I get peak.html  :)
So next challenge is [http://www.pythonchallenge.com/pc/def/peak.html](http://www.pythonchallenge.com/pc/def/peak.html)