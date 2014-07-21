---
layout: post
title: "Python的类型判别"
date: 2013-11-08 10:42
comments: true
categories: Python 
---
以前在Python里面判别类型会使用type()
{% codeblock Check type by using type() lang:pycon %}
num = 6
type(num)
{% endcodeblock %}


其实还有isinstance()
{% codeblock Check type by using isinstance() lang:pycon %}
line = u'你好'
isinstance(line, unicode)
{% endcodeblock %}

甚至还能这样使用 isinstance(line, (unicode, str))
  
因为最近在开发网站所以会经常碰到unicode的问题所以还蛮频繁的需要检查类型
