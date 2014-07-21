---
layout: post
title: "Coder 出错了"
date: 2013-12-17 00:32
comments: true
categories: Raspberry Pi 
---
一直因为忙于Project 而挺久没有玩Pi了 Pi就一直勤劳的帮我“挖矿”  

现在Project结束了 空闲些了 可以玩玩Pi了  

前段时间有看Tweet 发现Google有出一个Project叫Coder 用于Pi的  

可以把Pi迅速变成Web server  

刚想到就立马Google了下 找到了Coder的页面 根据页面提示把安装包给下载了下来  

{% img https://dl.dropboxusercontent.com/u/23849021/Blog/Picture/Raspberry%20Pi/Coder/Screen%20Shot%202013-12-17%20at%2012.44.09%20AM.jpg %}  

跟Raspbian很类似 把SD卡格式化下 然后插入Pi中就可以工作了 

根据步骤一步步来 没一会就出错了 

想了想可能是SD卡开了读写保护了， 把SD卡弹了出来， 发现黄色的读写保护按钮“高高”的停在unlock状态  

无奈的把它拨动到lock状态又拨回来  

再次运行Coder 不一会又出错了  

没办法 只好通过Disk Utility重新Format了下SD卡 再试 结果还是出错  

也许是Disk Utility的问题吧 然后拿出了“大杀器” SDFormater  

本以为没问题了 结果还是报错  

在万般无奈的情况下只好在Terminal中运行Coder的安装程序 

{% img https://dl.dropboxusercontent.com/u/23849021/Blog/Picture/Raspberry%20Pi/Coder/Screen%20Shot%202013-12-17%20at%201.02.37%20AM.jpg %}  

发现原来是因为Coder在执行脚本的时候文件夹名字的空格没有处理好所以一直报错 

如上图，  我的路径是/Volumes/Bu/Raspberry Pi/
而执行脚本的时候指向的却是/Volumes/Bu/Raspberry  

想到了以前Gmail也出现过一段时间的crash 最终是因为一个“／” 没想到Coder会因为一个“space”导致报错  

