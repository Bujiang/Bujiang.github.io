---
layout: post
title: "VIM 插件"
date: 2013-12-10 16:26
comments: true
categories: VIM 
---
在有了这些插件以后让VIM的使用可以变成一件很快乐而且高效率  

VIM插件的“管家”  

[Vundle](https://github.com/gmarik/vundle)  

Vundle 本身也属于VIM的一个插件 但是使用它可以很方便的管理其它VIM插件 例如在Github上发现好的VIM插件后 在vimrc里面添加一行代码后 Vundle就能帮我们安装需要的这个插件了 对于VIM新手来说实在是方便  

安装步骤：

1.在Terminal中使用Git来下载在Github上的Vundle 

{% codeblock %}
git clone https://github.com/gmarik/vundle.git ~/.vim/bundle/vundle
{% endcodeblock %}

2.通过编辑器打开vim设置文件

vim ~/.vimrc 

在设置文件的最上端添加一下代码
{% codeblock %}
set nocompatible
filetype off
set rtp+=~/.vim/bundle/vundle/
call vundle#rc()
" let Vundle manage Vundle
" required! 
Bundle 'gmarik/vundle'
"new plugin add below
filetype plugin indent on
{% endcodeblock %} 

以后安装新的VIM插件就只需要打开VIM设置文件 中添加 Bundle '插件在Github上的名字' 

添加好后 保存退出 再打开VIM 输入 :BundleInstall  

Vundle就会下载插件了

{% img https://dl.dropboxusercontent.com/u/23849021/Blog/Picture/Vim/Vim%20plugin/Screen%20Shot%202013-12-10%20at%205.09.43%20PM.jpg %}

一些我常用的插件都是通过vundle来安装的

EasyMotion 可以很方便的让光标移动到想要去的位置

默认按键有

\j   
\k   
\l  
\h

NERDTree 可以是文件夹和文件呈现成树状图 方便查找打开 默认使用vim的移动按键 和 o来打开文件或文件夹


