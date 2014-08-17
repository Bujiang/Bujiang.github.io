---
layout: post
title: "Python Challenge 2"
date: 2014-08-17 14:47:57 +0800
comments: true
categories: [Python,]
---

Stage 2

After finish load the [webpage](http://www.pythonchallenge.com/pc/def/ocr.html), there are a blurry picture and a paragraph 
{% blockquote %}
recognize the characters. maybe they are in the book, 
but MAYBE they are in the page source.
{% endblockquote %}

Perhaps the answer contain in the page source code, so I open terminal and in python interactive mode.
``` python
>>> import urllib2
>>> dir(urllib2)
['AbstractBasicAuthHandler', 'AbstractDigestAuthHandler', 'AbstractHTTPHandler', 'BaseHandler', 'CacheFTPHandler', 'FTPHandler', 'FileHandler', 'HTTPBasicAuthHandler', 'HTTPCookieProcessor', 'HTTPDefaultErrorHandler', 'HTTPDigestAuthHandler', 'HTTPError', 'HTTPErrorProcessor', 'HTTPHandler', 'HTTPPasswordMgr', 'HTTPPasswordMgrWithDefaultRealm', 'HTTPRedirectHandler', 'HTTPSHandler', 'OpenerDirector', 'ProxyBasicAuthHandler', 'ProxyDigestAuthHandler', 'ProxyHandler', 'Request', 'StringIO', 'URLError', 'UnknownHandler', '__builtins__', '__doc__', '__file__', '__name__', '__package__', '__version__', '_cut_port_re', '_opener', '_parse_proxy', '_safe_gethostbyname', 'addinfourl', 'base64', 'bisect', 'build_opener', 'ftpwrapper', 'getproxies', 'hashlib', 'httplib', 'install_opener', 'localhost', 'mimetools', 'os', 'parse_http_list', 'parse_keqv_list', 'posixpath', 'proxy_bypass', 'quote', 'random', 'randombytes', 're', 'request_host', 'socket', 'splitattr', 'splithost', 'splitpasswd', 'splitport', 'splittag', 'splittype', 'splituser', 'splitvalue', 'sys', 'time', 'toBytes', 'unquote', 'unwrap', 'url2pathname', 'urlopen', 'urlparse', 'warnings']
>>> page = urllib2.urlopen("http://www.pythonchallenge.com/pc/def/ocr.html")
>>> dir(page)
['__doc__', '__init__', '__iter__', '__module__', '__repr__', 'close', 'code', 'fileno', 'fp', 'getcode', 'geturl', 'headers', 'info', 'msg', 'next', 'read', 'readline', 'readlines', 'url']
>>> page = page.read()
```
urllib2 is python package that can open url (make request), but I can not remember exactly the function to access. 

By use dir(urllib2) it shows has urlopen which is 
needed one.

Ater I printed out the source code of the webpage, it mess up with a bunch of puctuation. It seems I am on the wrong track or this puctuations are some ciphertext? After a while, I recheck that paragraph it ask me to recognize the characters, so maybe it need the alphabets.
``` python
>>> charList = []
>>> for i in page:
...     if i.isalpha():
...             charList.append(i)
... 
>>> charList = ''.join(charList)
>>> charList
'htmlheadtitleocrtitlelinkrelstylesheettypetextcsshrefstylecssheadbodycenterimgsrcocrjpgbrfontcolorcrecognizethecharactersmaybetheyareinthebookbrbutMAYBEtheyareinthepagesourcecenterbrbrbrfontsizecolorgoldGeneraltipsliUsethehintsTheyarehelpfulmostofthetimesliliInvestigatethedatagiventoyouliliAvoidlookingforspoilerslibrForumsahrefhttpwwwpythonchallengecomforumsPythonChallengeForumsareadbeforeyoupostbrIRCircfreenodenetpythonchallengebrbrToseethesolutionstothepreviouslevelreplacepcwithpcciegotohttp

wwwpythonchallengecompccdefocrhtmlbodyhtmlfindrarecharactersinthemessbelowequality'
```

I find the tail of the whole string, it got "python challenge", "body html", "find", it seems interesting.
I open the source code of webpage in browser
``` html
<!--
find rare characters in the mess below:
-->

<!--
Inside this comment mess up with a bunch of puctuation
-->
```


Combine with "findrarecharactersinthemessbelowequality", I got the answer "equality"

So next state is [equality.html](http://www.pythonchallenge.com/pc/def/equality.html)