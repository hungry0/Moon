---
layout: post
title:  "Unity的一些骚操作"
date:   2018-11-06
excerpt: "Unity"
tag:
- [Tools]
comments: true
---

1. 当脚本继承自MonoBehavior但是没有实现Start和Update等方法，挂载在GameObject后就不会有那个对勾  

2. Shader中的枚举可以这样 **[Enum(UnityEngine.Rendering.CompareFunction)]**  

3. 实现新手引导那种挖洞效果时，需要两种Shader配合，目前项目是洞的Shader设置 ** Blend Zero One,Zero Zero ** 这是实现了挖洞的颜色显示。全局透明黑色背景色的实现是：洞的模板值填写一个值，然后不等于这个值的位置绘制就行了。洞的Stencil设置是Always Pass,全局背景的Stencil设置是NotEqual Pass。当实现点击时，需要屏蔽洞的点击事件，主要思路是： 继承** ICanvasRaycastFilter ** 方法实现过滤。  

