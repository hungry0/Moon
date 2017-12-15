---
layout: post
title:  "Unity中UGUI自定义点击区域"
date:   2017-12-15
excerpt: "Unity中UGUI自定义点击区域"
tag:
- [Unity UGUI]
comments: true
---
项目中由于有一些图片是不规则形状的，所以点击区域就会有误差，网上搜了一些方法如何自定义区域，有的很旧有的有问题，总结一下。  
主要思路是重写一下Image的判断点击是否有效的方法，查看官方文档是这个方法，[**public bool IsRaycastLocationValid(Vector2 sp, Camera eventCamera)。**](https://docs.unity3d.com/ScriptReference/UI.Image.IsRaycastLocationValid.html)  
自定义区域是使用一个叫[**Polygon Collider 2D**](https://docs.unity3d.com/ScriptReference/PolygonCollider2D.html)的组件，里边可以设定区域，指定顶点数量和位置就行了。（顶点位置是相对于该Image的本地坐标）  

代码如下。  
{% highlight c# %}
using System.Collections; 
using System.Collections.Generic; 
using UnityEngine; u
sing UnityEngine.UI;

[RequireComponent(typeof(PolygonCollider2D))] 
public class CustomButtonArea : Image 
{ 
    public override bool IsRaycastLocationValid(Vector2 screenPoint, Camera eventCamera) 
    { 
        return GetComponent<PolygonCollider2D>().OverlapPoint(eventCamera.ScreenToWorldPoint(screenPoint)); 
    } 
}
{% endhighlight %}

当前项目需要自定义按钮区域的地方
![custom-area](http://lizeyu.me/images/customBtnArea.png)