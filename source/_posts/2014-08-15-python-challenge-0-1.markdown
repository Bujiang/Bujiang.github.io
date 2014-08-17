---
layout: post
title: "Python challenge 0 - 1"
date: 2014-08-15 18:40:45 +0800
comments: true
categories: [Python, Bash]
---
Stage 0. Warming up

http://www.pythonchallenge.com/pc/def/0.html

The webpage contain a picture and show 2 to the power of 38, beneath the picture has a 
hint "try to change the URL address." 
This is a python challenge, so I open python in interactive mode, then calculate 
the answer. 
``` bash
>>> 2**38
274877906944
```

replace the 0 to result then get the next stage URL is http://www.pythonchallenge.com/pc/def/274877906944.html

Stage 1. What about making trans?

In webpage there have one picture and one paragraph. The picture show K->M O->Q E->G, and 
the paragraph looks like have some meaning but for now I do not know it.
I guess it probably is a caesar cipher. So in terminal(shell) I type man ascii to do
a quick check to confirm my guess. 'K', 'O', 'E' are all shift by two positions.
Then I write a shift function to decrypt it.
``` python
#!/usr/bin/env python

def change(ciphertext):
    plaintext = []
    for i in ciphertext:
        if i == ' ':
            plaintext.append(' ')
        elif i == '.':
            plaintext.append('.')
        elif i == '(':
            plaintext.append('(')
        elif i == ')':
            plaintext.append(')')
        elif i == '\'':
            plaintext.append('\'')
        else:
            # ASCII lower letter decimal value for a to z is 97 to 122
            value = ord(i) + 2

            if value > 122:
                value = value - 122 + 96
                plaintext.append(chr(value))
            else:
                plaintext.append(chr(ord(i) + 2))
    return ''.join(plaintext)

paragraph = "g fmnc wms bgblr rpylqjyrc gr zw fylb. rfyrq ufyr amknsrcpq ypc dmp. bmgle gr gl zw fylb gq glcddgagclr ylb rfyr'q ufw rfgq rcvr gq qm jmle. sqgle qrpgle.kyicrpylq() gq pcamkkclbcb. lmu ynnjw ml rfc spj."
decodedParagraph = change(paragraph)
print decodedParagraph
```

The result is below
``` bash
i hope you didnt translate it by hand. 
thats what computers are for. 
doing it in by hand is inefficient and that's why this text is so long. 
using string.maketrans() is recommended. 
now apply on the url.
```

oops, it seems instead of doing lines of coding, it just need a string function.
This stage URL is http://www.pythonchallenge.com/pc/def/map.html
map need to change to ocr, so get next stage URL 
http://www.pythonchallenge.com/pc/def/ocr.html

``` python
ciphertext = "map"

plaintext = string.maketrans(
    "abcdefghijklmnopqrstuvwxyz", "cdefghijklmnopqrstuvwxyzab"
)

print ciphertext.translate(plaintext)
```
