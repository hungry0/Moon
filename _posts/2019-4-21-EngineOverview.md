---
layout: post
title:  "UnrealEngine基础篇-EngineOverview"
date:   2019-04-21
excerpt: "UnrealEngine Basic"
tag:
- [UnrealEngine]
comments: true
---

## EngineOverview总结

PPT从UE官网下载的。

### 路径介绍

引擎根目录下

- /Engine - 引擎所有的代码、资源和配置
- /Templates - 一些模版项目，例如3D射击、2D游戏  

Engine路径下

- /Binaries - 可执行文件和Dlls库文件
- /Builds - 构建引擎所需的文件
- /Configs - 配置文件
- /Content - 引擎内置的一些资源，其中包括Editor的界面图素等等
- /DerivedDataCache - 缓存的一些引擎编译后数据（仅读）
- /Intermediate - 临时的构建文件（仅读）
- /Plugins - 插件
- /Saved - 本地配置文件、截图等
- /Source - 源码，包括运行时源码、Editor源码、插件等等

### INI Files

- 存储类的默认属性
- 开始启动时加载到CDOs
- 以层级方式管理
- 更高级别的将覆盖低级别的
- 以sections方式管理
- 在内部以监制对存储（Key-value）
- 重要的将暴露在Editor中
- FConfig可以访问

[^UE官方说：旧版本需要经常编辑INI文件，从Unreal Engine 4版本开始暴露出了一些重要的，未来版本争取做到不用手动编写INI文件。]: 

### INI文件格式

![INIDemo](http://lizeyu.me/images/INIDemo.png)

![INIDemo1](http://lizeyu.me/images/INIDemo1.png)Sections for UObjects

- [/Script/ModuleName.ClassName]

Sections for Custom Settins

- [SectionName]

Supported Value Types

- 数值类、字符串、枚举

- 结构体

- 静态和动态数组

  [^UObjects的变量或者说属性自动序列化]: 

### 模块类型

- Developer - Editor和Programs使用，游戏本身不能使用
- Editor - 仅供编辑器使用
- Runtime - 编辑器和Programs和游戏均可使用
- ThirdParty - 第三方公司的
- Plugins - 编辑器和游戏的扩展
- Programs - 主机和主机工具

### 模块依赖规则

- 运行时模块不能依赖编辑器和Developer模块
- Plugins模块不能依赖其它的模块

不同应用程序之间的模块引用如下图。

![ModuleRule](http://lizeyu.me/images/ModuleRule.png)

### 基础模块

- Core - 一些基础的类和方法
- CoreUObject - UObject的子系统的一些实现
- Engine - 游戏类和引擎框架
- OnlineSubSystem - 在线和社交
- Slate - 界面

### 进阶模块

- DesktopPlatform - 一些有用的API，有Windows平台、Mac和Linux
- DetailCustomizations - 编辑器的详细面板和定制
- Launch - 主循环的方法和类
- Messaging - 消息传递子系统
- Sockets - 联网实现
- Settings - 编辑器和项目设置API
- SlateCore - 基础UI方法
- TargetPlatform - 平台抽象层
- UMG - Unreal Motion Graphics实现（UI模块）
- UnrealEd - Editor主框架

### 有趣的模块

- Analytics - 收集编辑器和游戏的使用状态
- AssetRegistry - 编辑器的一些状态存储
- GameLiveStreaming - 直播流（PS：不是很懂，以后确认补上）
- HeadMountedDisplay - 头戴设备
- JsonUtilities & XmlParser - 数据处理
- SourceControl - 源代码管理











