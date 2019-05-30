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

- 蓝图的功能可以加进方法和常量。
- 可以存在于蓝图库中，供所有蓝图调用。
- 可以用C++封装。
- 非常普遍。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_29%201.png?raw=true)

- 蓝图之间交互。
- 在许多不同类之间进行日常交互。
- 替代Casting，并且更有效率。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_30%201.png?raw=true)

做数据相关的交互也比较方便

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
3.  类与类之间是否交互。
4.  是否把内存和性能考虑在内了。
5. 扩展性是否好。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_37%201.png?raw=true)

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_42%201.png?raw=true)

前边说了一大堆，一句话就是逻辑很复杂，要考虑好扩展性。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_43%201.png?raw=true)

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_44%201.png?raw=true)

- 不要把事情搞复杂。
- 平衡好新用法和需求。
- 一句话就是说扩展性要好。
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

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_93%201.png?raw=true)

- 蓝图对内存消耗和加载时间的影响很大
- **蓝图被认为是资源**
- C++是在启动时全部加载，而蓝图是需要的时候加载，和Mesh等无异。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_94%201.png?raw=true)

大概就是资源也是在需要的时候才加载，而蓝图属于资源。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_95%201.png?raw=true)

- 右键资源-Reference Viewer可以显示资源引用的资源，左上角可以设置深度。
- 并且会先加载应用的资源，例如材质引用了图片，先加载图片。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_97%201.png?raw=true)

- 蓝图引用的任何形式的资源都会加载进内存。
-  如果蓝图中有很多引用，那么很可能均加载。
-  Cast转换也是引用，意思就是也会加载。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_98%201.png?raw=true)

需要管理好引用，如果数量巨大，可以考虑拆分到子蓝图中。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_101%201.png?raw=true)

在资源上右键-Size Map可以显示这个资源加上它所引用资源的大小。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_102%201.png?raw=true)

可以提前指定好引用规则：

- 关键类用C++实现。
- 蓝图继承。
- 蓝图在继承蓝图。

设定Cast的规则。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_103%201.png?raw=true)

这个就是满足上面规则的继承树。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_104%201.png?raw=true)

方法库也一样，被引用的话也是全部加载，所以方法库应该只关注逻辑，尽量不引用资源。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_105%201.png?raw=true)

有资源引用，最右侧的粒子系统。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_106%201.png?raw=true)

没有资源引用，放到了参数中，动态设定。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_107%201.png?raw=true)

GameMode拆分也有助于降低内存占用和加载时间长。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_108%201.png?raw=true)

可以动态加载。软引用可以控制资源加载时机更精确。（软引用在Reference Viewer中是淡红色线连接。）图示中是使用**Async Load Asset**实现软引用。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_110%201.png?raw=true)

如果有大量可配置项，软引用是唯一的方法。可以通过使用Map来管理。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_112%201.png?raw=true)

编辑器的加载时间不具有参考性，以最终的包为准。

### Garbage Collection(GC)

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_114%201.png?raw=true)

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_113%201.png?raw=true)

GC就是清理不再使用的对象。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_116%201.png?raw=true)

不使用时会标记，引擎会遍历所有的对象找到需要清除的，然后清理它们占用的内存空间。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_117%201.png?raw=true)

GC因为需要遍历所有物体，所以是一个很耗时的操作。不过一般不用考虑这个，引擎都做了，除非一下子创建或者销毁很多物体。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_118%201.png?raw=true)

使用池避免创建和销毁。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_120%201.png?raw=true)

虚幻是每隔一段时间扫描一次，可以在设置中修改，默认是61s。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_121%201.png?raw=true)

不建议开启Cluster，可以移到C++中。

## Compilation

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_122%201.png?raw=true)

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_123%201.png?raw=true)

是什么影响了编译时间、迭代时间等。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_124%201.png?raw=true)

- 编译时间不影响运行时间。
- 影响迭代时间的原因是项目大。
- 引用关系影响内存和加载时间。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_125%201.png?raw=true)

影响编译时间的因素有：

- 蓝图中的节点数量。
- Casting和其它的引用数量。
- 循环引用。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_127%201.png?raw=true)

蓝图有一些上限，但是不用关心，如果超出了，肯定是自己的问题。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_128%201.png?raw=true)

最糟糕的情况是节点太多。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_129%201.png?raw=true)

宏是直接插到蓝图中编译的，偶尔会有用，不过没必要故意的使用。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_130%201.png?raw=true)

- 把功能拆分到子蓝图中。
-  Casting也能关键。
- 在大项目中，都是移植到C++中。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_131%201.png?raw=true)

蓝图的节点数量对编译速度很关键。Cast的对象会先被编译，然后才轮得上本蓝图编译。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_134%201.png?raw=true)

引用一个对象和Cast的效果是一样的。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_135%201.png?raw=true)

对内存的影响比编译速度的影响更严重。

### The good and bad casting

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_136%201.png?raw=true)

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_137%201.png?raw=true)

Cast和引用应该谨慎，尽可能的减少使用。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_138%201.png?raw=true)

- 强转为Pawn一般情况没问题，因为player类一直在内存中。
- 其它框架类也一般ok。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_140%201.png?raw=true)

把任何蓝图强转到一个只含变量的蓝图是可以的，因为不会影响编译速度和内存占用。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_141%201.png?raw=true)

强转为一个很少使用的蓝图不好，尤其是它包含很多功能。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_142%201.png?raw=true)

在框架类之间来回转换，对内存来说没啥影响，不过编译时间可能受影响。因为它需要编译所有的类，如果修改了其中一个。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_144%201.png?raw=true)

核心类一直在内存中，其余不是。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_145%201.png?raw=true)

- 设计一个系统决定何时以及在哪可以Cast。
- 设计一些类可以无损耗的强转的。
- 最小化依赖链。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_146%201.png?raw=true)

使用C++作为桥梁，并且可以使蓝图更清晰。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_148%201.png?raw=true)

利用好事件系统。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_150%201.png?raw=true)

强转为父类没有任何损耗。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_151%201.png?raw=true)

利用好接口，也可以降低Cast和引用的数量。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_152%201.png?raw=true)

接口明显不用Cast。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_153%201.png?raw=true)

检查一个Actor是否是特定类也是一次引用，所以可以查Tag，这样可以避免一次强转咯。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_154%201.png?raw=true)

最好的方式是一些混合：

- 好的Cast策略 + C++ + 接口 + 继承。
- 一些tags。

### Race Conditions

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_155%201.png?raw=true)

介绍下编译时竞争条件。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_156%201.png?raw=true)

互相引用造成的问题。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_158%201.png?raw=true)

小心蓝图的初始化顺序。（这个咋小心？）

是否有效的检测可能出发竞争条件。

如果很多蓝图互相引用，很容易出现这种情况。

## C++

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_159%201.png?raw=true)

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_160%201.png?raw=true)

所有的蓝图节点的实现都是C++。很容易用蓝图扩展C++；

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_161%201.png?raw=true)

大型项目的C++可能占百分之80，不过因项目而异。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_162%201.png?raw=true)

从蓝图开始，而精于C++；

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_163%201.png?raw=true)

- 效率高。
- 易管理。
- Save Games、SDK、平台差异等不能用蓝图或者不方便。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_164%201.png?raw=true)

- 蓝图易于出原型。
- 迭代快。
- 易于理解。
- 弹性好。
- 更适用于引用资源。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_165%201.png?raw=true)

还是那句话，C++做功能，蓝图扩展。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_166%201.png?raw=true)

这些情况需要使用C++：

- 很多地方使用。
- 每帧都调用。
- 很容易出Bug的地方。
- 以后极有可能扩展的。
- Save Games、网络等方面。
- 重要的变量或者枚举等。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_169%201.png?raw=true)

使用pure functions（不知道怎么翻译好）优化工作流。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_170%201.png?raw=true)

如果很多蓝图都需要访问，那么用C++的静态方法很好。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_171%201.png?raw=true)

如果大部分方法是用C++实现，那么应该提供回调和事件。及时暂时用不上。

## Miscellaneous

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_172%201.png?raw=true)

一些杂项。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_173%201.png?raw=true)

标为DOP的节点是故意不连接的。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_174%201.png?raw=true)

使用纯函数使代码整洁一些。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_175%201.png?raw=true)

暴露出入口，这样新建Actor时就可以设置值。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_176%201.png?raw=true)

自定义事件可以勾选Call In Editor，这样Editor中也可以调用。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_177%201.png?raw=true)

暴露给Cinematics。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_178%201.png?raw=true)

删除无用的变量。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_180%201.png?raw=true)

可以在蓝图中标记为过时，这样扔可以使用，不过不可编辑了。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_181%201.png?raw=true)

类似于一个标记，可以快速跳转过去。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_182%201.png?raw=true)

- 和Data tables类似并且可以从CSV格式导入。
- 可以用来做国际化。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_183%201.png?raw=true)

Maps可以运行时修改。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_184%201.png?raw=true)

Sets和Arrays类似，不过里面的值唯一。

![](https://github.com/hungry0/Study_Books/blob/master/Books/Blueprint%20In-Depth/Images/Snip20190529_185%201.png?raw=true)

在使用对象之前，切记检测，否则崩溃。












