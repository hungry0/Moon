---
layout: post
title:  "Blueprint In-Depth"
date:   2019-05-30
excerpt: "UnrealEngine Basic"
tag:
- [UnrealEngine]
comments: true
---

# Blueprint In-Depth

在Youtube上看到一篇Epic的分享，学习到了很多，因为目前ppt并没有公开，而且官方网站的资源部分已经很久不更新了，所以不抱能及时看到的希望，大佬围绕蓝图从六个方面进行了长达两个多小时的分享，脸不红气不喘，很佩服。

- [点此进入Youtube主页](https://www.youtube.com/watch?v=j6mskTgL7kU)
- 发布时间是2019年5月20日
- 作者是Sjoerd De Jong(神一样的人物)

##  Introduction

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_8%201.png?raw=true)

在虚幻中很多东西都是围绕蓝图展开的，刚开始使用虚幻是很简单的。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_9%201.png?raw=true)

如何用可扩展性高且性能好的方式使用蓝图。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_12%201.png?raw=true)

蓝图的编辑界面也很好理解。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_13%201.png?raw=true)

现在还使用蓝图的三个原因是：**不会过时、合作、性能**。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_16%201.png?raw=true)

几个术语的解释。

## Feature Overview

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_17%201.png?raw=true)

一张大纲图提领全文。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_19%201.png?raw=true)

蓝图和图示几个方面均有关联。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_20%201.png?raw=true)

- C++可以和蓝图无缝结合使用
- 逻辑可以放C++端或者蓝图端
- 更好的性能
- 大项目C++更适合合作
- 可以做蓝图不能做的。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_21%201.png?raw=true)

继承允许扩展或者覆盖父类的方法等。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_22%201.png?raw=true)

游戏框架是基础，使用广泛，并且使用多少因项目而异。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_23%201.png?raw=true)

组件一般是为了实现特定需求而使用。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_24%201.png?raw=true)

不常用，但是比组件更强大。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_25%201.png?raw=true)

- 蓝图的功能可以加进方法和常量
- 可以存在于蓝图库中，供所有蓝图调用。
- 可以用C++封装。
- 非常普遍。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_29%201.png?raw=true)

- 蓝图之间交互
- 在许多类之间更通用。
- 替代Casting，并且更有效率。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_30%201.png?raw=true)

做数据相关的交互比较方便

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_31%201.png?raw=true)

- 类仅含数据
- 在常规类外使用
- 在不同类之间分享数据

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_32%201.png?raw=true)

一个总得结构图。

## The Big Picture

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_33%201.png?raw=true)

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_34%201.png?raw=true)

当会使用之后，挑战就变成了如何做的正确、整洁、有效。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_35%201.png?raw=true)

功能的总体架构。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_36%201.png?raw=true)

1. 是否做的足够简洁。
2. 是否好理解。
3.  ----------------------没看懂
4.  是否把内存和性能考虑在内。
5. 扩展性是否好。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_37%201.png?raw=true)

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_42%201.png?raw=true)

前边说了一大堆，一句话就是逻辑很复杂，要考虑好扩展性。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_43%201.png?raw=true)

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_44%201.png?raw=true)

- 不要把事情搞复杂。
- 平衡好新用法和需求。
- 一句话就是延展性或者说扩展性。
- 性能和稳定，不断考虑如何避免bug。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_45%201.png?raw=true)

合理的架构也有利于大家使用蓝图时之间的合作。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_46%201.png?raw=true)

一个合理的蓝图的继承图。就是C++实现功能，蓝图用于做填空题，例如在C++中做好各种事件的回调，做好例子系统音效等的引用，在蓝图中指定和实现需要的回调。

## Performance

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_47%201.png?raw=true)

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_48%201.png?raw=true)

即便性能不是问题，关注蓝图造成的开销也可以更深入的了解这个东西。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_49%201.png?raw=true)

蓝图虽然比C++慢那么一丢丢，但是把功能移植到C++的原因是为了多人协作。不过，用不好的话，蓝图确实很有性能问题。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_50%201.png?raw=true)

蓝图比C++慢十倍之多，不过是在某些特定条件下。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_51%201.png?raw=true)

- 性能问题可能是因为大量的节点。
- 逻辑复杂或者计算问题在蓝图中比较费资源。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_52%201.png?raw=true)

应该是说只有只有两个节点，所以执行速度相同。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_53%201.png?raw=true)

尽量避免循环。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_54%201.png?raw=true)

大佬建议将这种需要遍历的放到C++中。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_55%201.png?raw=true)

tick比C++中更费资源，并且tick的滥用是蓝图性能低的主要原因。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_56%201.png?raw=true)

如果性能问题很重要，就彻底不要使用tick。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_59%201.png?raw=true)

蓝图在一个线程中执行，并且最大指令数是250000，在一次tick中。大佬说知道这个也毫无卵用，几乎碰不到超了的情况。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_60%201.png?raw=true)

将多个mesh放到一个蓝图中，对蓝图性能没有影响。就算有影响也是自身Mesh带来的。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_61%201.png?raw=true)

不同的环境蓝图的性能也是不同的。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_62%201.png?raw=true)

可能会看不清楚，一个for循环里边有一些数学运算。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_63%201.png?raw=true)

蓝图和C++的表现差距还是很明显的。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_64%201.png?raw=true)

即使是蓝图自身，在不同的环境下性能也不一样

### Ticking

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_65%201.png?raw=true)

花了很大篇幅讲解tick怎么优化。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_66%201.png?raw=true)

tick方法不是唯一的每帧执行的，还有Timeline，一些交互输入。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_67%201.png?raw=true)

动画更新和UMG。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_68%201.png?raw=true)

慎用tick，并且90%的情况能找到替代tick实现的方法。**甚至可以在设置中禁用蓝图默认tick**。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_69%201.png?raw=true)

Timers和Events可以搭配使用替换Tick，很常用。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_70%201.png?raw=true)

当使用Timers时，可以设置一个随机的偏移量，以避开同时update引起的峰值。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_71%201.png?raw=true)

只有确定需要刷新内容的时候才改变。（例子是UMG更新一个Text）

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_72%201.png?raw=true)

- 可以关掉Tick，不过如果没有使用，就相当于关掉了。
- 可以修改频率。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_73%201.png?raw=true)

可以有条件的开启Tick里的刷新。这里是根据距离。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_74%201.png?raw=true)

使用SetActorTickInterval设置更新频率。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_75%201.png?raw=true)

是否被渲染控制。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_76%201.png?raw=true)

逻辑和渲染分开，逻辑可以更新更慢。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_77%201.png?raw=true)

碰撞检测比较影响性能，所以使用Timer。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_78%201.png?raw=true)

材质每帧更新。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_79%201.png?raw=true)

一些效果可以移到材质中，例如旋转。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_81%201.png?raw=true)

可以把任意的Tick移到C+++，不过可以先测试一下确实有益于性能。

###  Profiling and Debuging

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_83%201.png?raw=true)

在最上面工具栏有调试选项。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_85%201.png?raw=true)

右键选中变量，选择Watch，然后在编辑器上可以打开Blueprint Debuger的Watches。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_88%201.png?raw=true)

继承自Functional Test的蓝图，实现自动测试功能。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_89%201.png?raw=true)

内置命令台——stat game

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_90%201.png?raw=true)

显示执行Tick的Actor

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_91%201.png?raw=true)

使用内置profiler是最精确的了。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_92%201.png?raw=true)

使用自动化测试流程测试指定的蓝图逻辑。（这个需要看Youtube的视频演示了）

### Memory and Loading

### Garbage Collection(GC)

## Compilation

## C++

## Miscellaneous












