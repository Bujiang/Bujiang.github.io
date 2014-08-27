---
layout: post
title: "Python challenge 6"
date: 2014-08-25 20:12:12 +0800
comments: true
categories: [Python,]
---
Challenge 6. [now there are pairs](http://www.pythonchallenge.com/pc/def/channel.html)

Only one image, a zipper opened jeans, file in web page. As usual to check the source code.
``` html
<html> <!-- <-- zip -->
<head>
  <title>now there are pairs</title>
  <link rel="stylesheet" type="text/css" href="../style.css">
</head>
<body>
<center>
<img src="channel.jpg">
<br/>
<!-- The following has nothing to do with the riddle itself. I just
thought it would be the right point to offer you to donate to the
Python Challenge project. Any amount will be greatly appreciated.

-thesamet
-->

<form action="https://www.paypal.com/cgi-bin/webscr" method="post">
    <input type="hidden" name="cmd" value="_xclick">
    <input type="hidden" name="business" value="thesamet@gmail.com">
    <input type="hidden" name="item_name" value="Python Challenge donations">
    <input type="hidden" name="no_note" value="1">
    <input type="hidden" name="currency_code" value="USD">
    <input type="hidden" name="tax" value="0">
    <input type="hidden" name="bn" value="PP-DonationsBF">
    <input type="image" src="https://www.paypal.com/en_US/i/btn/x-click-but04.gif" border="0" name="submit" alt="Make payments with PayPal - it's fast, free and secure!">
    <img alt="" border="0" src="https://www.paypal.com/en_US/i/scr/pixel.gif" width="1" height="1">
</form>

</body>
</html>
```

Nothing special, the head, title, body, except an donate form. But the comment in the middle of markup code indicate only above it belongs to challenge 6. So let's analyze line by line. First line is opening html tag, second line is head tag, third line is a title tag with "now" ther are pairs inside, next line is css link, next line is closing head tag, next is body tag, next is a center img.
Now the only thing I have left is the comment after the html opening tag

``` html 
<!-- <-- zip -->
```
Maybe this challenge is not channel.html, but channel.zip? After change html to zip in browser, surprisingly find there do exist the zip file. 

``` bash
~/Desktop/channel ➤ cat readme.txt 
welcome to my zipped list.

hint1: start from 90052
hint2: answer is inside the zip
```
Unzip the file and find it has a readme.txt inside channel folder.
``` bash
~/Desktop/channel ➤ cat 90052.txt 
Next nothing is 94191~/Desktop/channel ➤ cat 94191.txt 
Next nothing is 85503~/Desktop/channel ➤ 
```
Like challeng 4 find the linked html, this time need to check the txt file.
``` python
import re

fileExtension = '.txt'
firstFileName = '90052'
digis = "\d+"

with open((firstFileName + fileExtension), 'r') as f:
    data = f.read()
    print data
f.close()
finding = re.search(digis, data)

while finding.group(0):
    nothingValue = finding.group(0)
    #In text file is like "Next nothing is ***", name the variable nothingValue
    with open((nothingValue + fileExtension), 'r') as f:
        data = f.read()
        print data
    f.close()
    finding = re.search(digis, data)
print data
```
``` bash
~/Desktop/channel ➤ python b.py 
Next nothing is 94191
............
Next nothing is 67824
Next nothing is 46145
Collect the comments.
```
I do a quick Google search for python file comment and find there is a zipfile module for python to work with archives. Use comment methond of ZipFile can get the comment.
``` python
import re, zipfile

fileExtension = '.txt'
firstFileName = '90052'
digis = "\d+"
commentList = []

channelZipfile = zipfile.ZipFile("channel.zip")

with open((firstFileName + fileExtension), 'r') as f:
    data = f.read()
    print data
f.close()
finding = re.search(digis, data)
commentList.append(channelZipfile.getinfo((firstFileName + fileExtension)).comment)
try:
    while finding.group(0):
        nothingValue = finding.group(0)
        #In text file is like "Next nothing is ***", name the variable nothingValue
        commentList.append(channelZipfile.getinfo((nothingValue + fileExtension)).comment)
        with open((nothingValue + fileExtension), 'r') as f:
            data = f.read()
            print data
        f.close()
        finding = re.search(digis, data)
except AttributeError:
    pass
print ''.join(commentList)
```
{% img https://dl.dropboxusercontent.com/u/23849021/Blog/Picture/Python/Python%20challenge%206/1.jpg %}


Next challenge is [hockey](http://www.pythonchallenge.com/pc/def/hockey.html)