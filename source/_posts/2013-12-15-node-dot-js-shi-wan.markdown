---
layout: post
title: "Node.js 试玩"
date: 2013-12-15 08:47
comments: true
categories: Node 
---
一般提到JavaScript都会想到网页前端， 通常JavaScript都是在浏览器中执行的  

而Node.js不同与一般JavaScript它是在服务器端执行（在V8引擎的虚拟机上）  

{% img https://dl.dropboxusercontent.com/u/23849021/Blog/Picture/Node.js/%E8%AF%95%E7%8E%A9/Screen%20Shot%202013-12-15%20at%208.56.25%20AM.jpg %}  

如上图 如果不带任何参数的执行node 就像Python一样会出现一个互动的界面 在这里可以执行JavaScript  

介绍完了 开始coding第一个小程序 hello.js  

{% codeblock %}  
setTimeout(function() {
    console.log("world");
}, 2000)
    console.log("hello");
{% endcodeblock %}  

{% img https://dl.dropboxusercontent.com/u/23849021/Blog/Picture/Node.js/%E8%AF%95%E7%8E%A9/Screen%20Shot%202013-12-15%20at%209.11.24%20AM.jpg %}  

执行hello.js  会先出现hello 在等待了2秒钟后会出现world  

＊： 把上面code中setTimeout 改成 setInterval  再执行hello.js 就会每间隔2秒显示一次world  

hello world 完了 现在来个简易的web server  

{% codeblock %}  
web-server.js
var http = require('http');

var s = http.createServer(function(req, res) {
    res.writeHead(200, { 'content-type': 'text/plain' });
    res.end("hello world\n");
}); 
s.listen(8000);
{% endcodeblock %}

上面的code 先让http载入http模块  然后创建server变量s  让s返回200 ok 以及 hello world给浏览器 在浏览器端输入ip地址加上8000端口就可以看到hello world了  

{% img https://dl.dropboxusercontent.com/u/23849021/Blog/Picture/Node.js/%E8%AF%95%E7%8E%A9/Screen%20Shot%202013-12-15%20at%209.31.15%20AM.jpg %}  

当然也可以通过curl来看header  

{% img https://dl.dropboxusercontent.com/u/23849021/Blog/Picture/Node.js/%E8%AF%95%E7%8E%A9/Screen%20Shot%202013-12-15%20at%209.36.23%20AM.jpg %}  


