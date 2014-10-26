---
layout: post
title: "Interesting looping methods in Ruby"
date: 2014-10-26 14:40:51 +0800
comments: true
categories: Ruby 
---
In Python most the time I use for loop method to iterating list, like the code below
``` python
for num in xrange(10):
    print num,

0 1 2 3 4 5 6 7 8 9
```
But in Ruby there are more ways to play with

like Ptyhon one for loop
``` ruby
for num in (0..9)
    print num, ' '
end
```

Ruby way
``` ruby
(0..9).each do |num|
    print num, ' '
end
```

one line
``` ruby
(0..9).each { |num| print num, ' '}
```
