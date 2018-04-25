---
layout: post
title:  "XUPorter中弱引用frameworks"
date:   2017-12-15
excerpt: "XUPorter中弱引用frameworks"
tag:
- [Xcode]
comments: true
---

在接iosSDK时，项目使用了XUPorter这个插件自动引用frameworks，由于各种奇奇怪怪的问题，所以需要弱引用frameworks，经过请教读书哥和查看源代码，记录一下下。  

源码如下。

```
foreach( string framework in mod.frameworks ) {
	string[] filename = framework.Split( ':' );
	bool isWeak = ( filename.Length > 1 ) ? true : false;
	string completePath = System.IO.Path.Combine( "System/Library/Frameworks", filename[0] );
	this.AddFile( completePath, frameworkGroup, "SDKROOT", true, isWeak );
}
```

因为它是在读.projmods这个配置文件时，判断是否有以冒号为分隔符的字段，所以读书哥说的**Security.framework:weak**是非常完美的。