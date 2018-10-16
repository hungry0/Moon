---
layout: post
title:  "RenderDoc遇到的一些问题"
date:   2018-10-16
excerpt: "RenderDoc遇到的一些问题"
tag:
- [Tools]
comments: true
---

1. 调试安卓设备连不上，报：Remote server not running or failed to start  

因为之前作死的拿的RenderDoc的源代码编译的32位（文档说32位可以抓64位和32位的包）exe使用的，所以网上搜出来结论是需要手动先安装一个
org.renderdoc.renderdoccmd.arm32.apk，但是编译的没这个，通过下载了一个RenderDoc安装包（msi），安装完毕以后就有这个apk了，装到手机就可以了。  
