---
layout: post
title: "Use SSHFS to mount remote file system"
date: 2014-08-28 22:19:11 +0800
comments: true
categories: [Bash,]
---
Be a lazy man sometimes may increase productivity a bit :) 
Everytime update my server I need to scp or use FileZilla to upload my updated files or new files. But I want a method that upload files to server just like copy to another directory. After I do some search, I find a tool named SSHFS(SSH Filesystem) can do the job. 
``` bash
sudo sshfs *****@xxx.xxx.xxx.xxx:/usr/share/nginx/html ~/ServerHTML
```