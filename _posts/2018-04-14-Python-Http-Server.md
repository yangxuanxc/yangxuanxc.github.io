---
layout:     post
title:      "一行python代码实现一个Http服务器，告别文件传输烦恼"
subtitle:   " \"小白也能学会的教程\""
date:       2018-04-12 14:00:00
author:     "二胖"
header-img: "img/about-bg-walle.jpg"
catalog: true
tags:
    - Python小教程

---

> 如果你有一个文件需要在两台linux服务器上进行传输你会怎么办？
> 
> 如果你需要将linux服务器上的文件传给不会编程的产品经理，你又会怎么办？

## 问题引入

![]({{ site.baseurl }}/img/2018-04/python_http_server/1.jpg)

不知道大家有没有遇到过这样的问题：在实际的开发过程中，很多时候我们都不直接在本机上进行开发，一般都是在远程服务器上开发运行程序。比如二胖在实际开发中就会使用到很多台服务器，简单来说就是我有一台笔记本电脑，通过ssh连接着很多台服务器[如上图所示]，我需要经常在不同的服务器上进行开发，所以很多时候就会遇到需要在不同的计算机之间传输文件的情景。可以归纳为以下几个情景：

1. 个人电脑和个人电脑之间传递文件。
2. 服务器之间进行文件传递。
3. 服务器与个人电脑（笔记本）之间进行文件传递。

## 解决办法？

我们先来说说第一点，个人电脑和个人电脑之间是如何传递文件的。个人电脑的操作系统基本都是图形界面的操作系统，比如Windows操作系统和MacOs操作系统，最简单的办法呢就是打开电脑QQ或者电脑微信进行传递即可，是不是感觉二胖在说废话啊？嘿嘿，我感觉也是的，不过为了让文章更加完整，二胖还是提及一下。其实很多公司内部都有自己的即时聊天系统软件，一般不会用QQ和微信等第三方软件来进行数据传输，不过道里都是一样的。

好啦，现在来讨论第二点，服务器与服务器之间进行文件传递。我想大部分童鞋最长使用的是 scp 命令来进行文件传递的吧。

### scp命令是什么？

简单来说，Linux scp命令就是用于Linux之间复制文件和目录。

scp是 secure copy的缩写, scp是linux系统下基于ssh登陆进行安全的远程文件拷贝命令。

`scp [可选参数] file_source file_target`

因为今天主要讲的不是scp命令，在这里就不过多阐述了，想要了解的童鞋可以点击下面这个视频，二胖录了个小教程讲解scp命令的用法。

<iframe style="float:middle" width="650" height="400" src="http://player.youku.com/embed/XMzUzNjQxNTQ0OA==" frameborder="0" allowfullscreen></iframe>

今天的重磅是服务器与个人电脑之间的文件传递，相信很多同学这时候迫不及待的说：“直接rz，sz命令不就得了吗，至于那么麻烦吗？”。确实，sz/rz命令是linux服务器与ssh客户端进行文件的交互的命令，也就是上传和下载文件到服务器和本地。

`sz：将选定的文件发送（send）到本地机器`

`rz：运行该命令会弹出一个文件选择窗口，从本地选择文件上传到服务器(receive)`

确实，这两个命令是可以实现服务器与个人电脑之间上传下载文件的，不过有两个问题，当文件十分大的时候，对于部分电脑而言，sz/rz就会失败。还有一个问题就是，我们需要把文件传递给其他人，而不是从服务器上下载文件到本地，这该怎么解决？

这两个命令也不细讲，对linux命令行不太熟悉的童鞋可以关注我，之后我会录制linux系统基本使用的教程，到时候大家可以详细了解。现在我们继续了解第三种情况下，怎么用一行代码来搭建一个http服务器实现文件传输。

Python2：

`python -m SimpleHTTPServer prot`

Python3：

`python3 -m http.server prot`

下面就录制一个视频给大家讲讲。当然http服务如果只用来传文件就大材小用了，还可以用来作为一个web 服务器。

<iframe style="float:middle" width="650" height="400" src="http://player.youku.com/embed/XMzUzNjQxNTQ0OA==" frameborder="0" allowfullscreen></iframe>

用一行命令就运行了这个http server了，赶快来制作你的第一个网站吧。

![]({{ site.baseurl }}/img/2018-04/python_http_server/2.jpg)

## 完～


