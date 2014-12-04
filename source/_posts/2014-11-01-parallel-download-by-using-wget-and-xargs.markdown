---
layout: post
title: "通过Wget和Xargs并行下载"
date: 2014-11-01 21:53:24 +0800
comments: true
categories: bash 
---
前几天的36氪的WISE 1.0 互联网创业者大会 觉得还有点意思 准备把直播视频保存下来
通过分析网页 发现视频是m3u8(m3u的Unicode版本 类似于文本文件里面纪录了视频文件名）
里面包含了1500多个小视频 这要一个一个手动下载还不累死了

因为文件中只有视频文件名 没有完整的地址 我通过VIM的visual block在所有文件名前添加了地址

一切准备就绪后 就通过Wget和Xargs两个工具加上pipe进行下载了
``` bash
cat file.m3u8 | xargs -n 1 -P 20 wget
```

-n 1 即每次把一行（一个文件地址） 给wget下载

-P 20 表示最多同时运行20个wget （20个并行下载）
