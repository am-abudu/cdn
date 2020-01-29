---
title: IDM超线程
date: 2019-12-27 22:06:28
tags:
    - IDM
    - 多线程
    - 实用技巧
categories: 实用技巧
cover: https://i.loli.net/2019/12/27/JckgR3zQVM2AtrT.png
---
# 开始
![](https://i.loli.net/2019/12/27/JckgR3zQVM2AtrT.png)
IDM下载工具非常好用，如果你还不知道怎么下载，请看上一篇文章[点击转跳](https://abudu.ml/internetdownloadmanager/)。但是它也有一个致命缺陷：就是最大线程数只能到32，这使得在下载时不能达到最快，今天我们就来聊聊：**IDM超线程**。
## 思路
我们发现，IDM的线程数由注册表的 **HKEY_CURRENT_USER\Software\DownloadManager** 控制，我们只需要修改这个值就可以做到超线程。而这是一个十六进制数，我们修改时要注意转换
## 代码
创建一个.txt文件，把下文代码复制到此文件里，然后把文件后缀改成.reg，关闭所有IDM进程，双击运行即可。
64线程：
```cmd
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\DownloadManager]
"MaxConnectionsNumber"=dword:00000020
```
128线程：
```cmd
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\DownloadManager]
"MaxConnectionsNumber"=dword:00000080
```
256线程：
```cmd
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\DownloadManager]
"MaxConnectionsNumber"=dword:00000100
```
## 制作完成后的文件（小白福利）
当然了，会有一些小白不会，我这里把制作好的.reg文件分享出来
下载地址：[蓝奏云](http://t.cn/AiFbm23h) 密码：c40v
## 完成截图
![](https://i.loli.net/2019/12/27/ExwDXVSd4LsUMcR.png)
完成后应该是这样的，并不会显示UI，但是下载速度是有的！![](http://ww3.sinaimg.cn/large/9150e4e5ly1fsgu3282c1g208c08c74b.gif)
# 最后的最后
如果喜欢，别忘了Ctrl+D收藏本站哦
