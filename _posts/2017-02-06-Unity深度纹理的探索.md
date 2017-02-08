---
layout: post
title:  "Unity深度纹理的探索"
date:   2017-02-06
excerpt: "Unity中关于深度纹理的一些基础知识"
tag:
- [Unity Shader]
comments: true
---
我在实现阴影映射（Shadow Mapping）过程中，因为需要使用摄像机视角的深度纹理以及光源视角的深度纹理，所以查阅了一些关于深度纹理的使用以及实现其可视化的资料，特此记录。

### **什么是深度纹理**  

简单而言，深度纹理中存的是一个像素的z值（视锥体近平面与远平面之间的任何值），在此处就表示深度。但是，它的范围是0.0~1.0之间。这个距离是从摄像机为原点计算出来的z的值。然而它实际存储的值是经过mvp矩阵变换之后，即变换到摄像机空间（view space）又经projection矩阵变换(进入剪裁空间，也被称为齐次剪裁空间)之后在经硬件自动除以w（这之后才是真正的投影变换）<font color='red'>OpenGL中齐次除法之后的范围是-1~1</font>，最后得到的是归一化的设备坐标（Normalized Device Coordinate，NDC）。然后统一 z * 0.5 + 0.5之后，将范围变换到0~1，诺诺，存的就是此值了。

### **深度纹理精度问题的细节**
由于摄像机常用的far距离有时实在是太远，并且计算机的浮点数的精度限制，当一个很大的距离（例如0~2000）映射到0.0~1.0时，会有很大的误差。所以，就有了一种近处精度较高，远处精度较低的计算方法，参考[OpenGL教程中关于深度测试的一章](http://learnopengl-cn.readthedocs.io/zh/latest/04%20Advanced%20OpenGL/01%20Depth%20testing/)。

### **Unity中实现深度纹理的可视化**
Unity中封装了各种现成的函数供我们使用，尤其是着色器中的一些计算方法，虽然代码简单，但是值得摸索的东西还有很多。
实现思路如下：告诉Camera，本次渲染要渲染深度纹理，然后在Shader中使用Unity提供的纹理以及函数等实现深度纹理的可视化。下面先贴出脚本以及Shader的代码。

* 1.脚本通知Camera绘制深度纹理，代码如下。
{% highlight c# %}
using UnityEngine;
using System.Collections;

[ExecuteInEditMode]
[RequireComponent(typeof(Camera))]
public class ShowDepth : MonoBehaviour {

	public Material mat;

	void Start () {
		Camera.main.depthTextureMode = DepthTextureMode.Depth;
	}

	// Called by the camera to apply the image effect
	void OnRenderImage (RenderTexture source, RenderTexture destination){
		//mat is the material containing your shader
		Graphics.Blit(source,destination,mat);
	}
}
{% endhighlight %}  
脚本中遇到的迷惑。  
1.    这个相当于后处理效果，调用OnRenderImage方法。  
2.    需要显示告诉Camera，绘制深度纹理。（还有法线纹理可选择，官网有说明）。  



* 2.Shader的代码如下。
{% highlight c++ %}
Shader "Custom/ShowDepth" {
SubShader {
Tags { "RenderType"="Opaque" }

Pass{
CGPROGRAM
#pragma vertex vert
#pragma fragment frag
#include "UnityCG.cginc"

sampler2D _CameraDepthTexture;

struct v2f {
   float4 pos : SV_POSITION;
   float4 scrPos:TEXCOORD1;
};

v2f vert (appdata_base v){
   v2f o;
   o.pos = mul (UNITY_MATRIX_MVP, v.vertex);
   o.scrPos = ComputeScreenPos(o.pos);
   return o;
}

half4 frag (v2f i) : COLOR{
   float depthValue = Linear01Depth (tex2Dproj(_CameraDepthTexture, UNITY_PROJ_COORD(i.scrPos)).r); //将非线性变换到线性，范围前后都是0~1
   half4 depth;

   depth.r = depthValue;
   depth.g = depthValue;
   depth.b = depthValue;
   depth.a = 1;
   
   return depth;
}
ENDCG
}
}
FallBack "Diffuse"
}
{% endhighlight %}  

Shader中遇到的疑惑较多，主要有以下几个部分。
-     **ComputeScreenPos计算完的结果是什么？**  
  这个结果是齐次除法之前的屏幕像素级别的屏幕坐标，在片元着色器中直接执行透视除法之后即是光栅化之后各个像素的具体位置。（范围依旧为-1~1）  
  
-     **为什么不在顶点着色器执行透视除法？**  
因为透视除法除以w时不是线性的，而光栅化往往是线性的，容易造成较大误差。  
  
-  **tex2Dproj(_CameraDepthTexture, UNITY_PROJ_COORD(i.scrPos)).r做了什么？**  
因为纹理采样时纹理坐标范围是0~1，所以这个函数的效果和tex2D(_CameraDepthTexture,i.srcPos * 0.5 + 0.5)效果一样。（PS：以前在Cocos2d-x中计算时都是自己算，谁知HLSL竟然有这种函数，懵逼ing...）  

- **为什么是红色通道存储深度呢？**  
直觉上是总得有一个通道存储。那么别的通道有没有存储有用的值呢？暂时未知只有深度纹理时gba通道的用处。不过当同时要使用深度和法线值（view space，即摄像机坐标系下）时，会合理使用rgba四个通道。官网的内容如下：  

    > This builds a screen-sized 32 bit (8 bit/channel) texture, where view space normals are encoded into R&G channels, and depth is encoded in B&A channels. Normals are encoded using Stereographic projection, and depth is 16 bit value packed into two 8 bit channels.  

- **如果深度纹理存的就是0~1的范围，那么为什么不能直接显示，而是使用Linear01Depth函数？**  
因为深度存储时不是线性的，而计算时往往使用的是线性的深度，所以需要变换到NDC空间坐标系下时z的坐标。下面是OpenGL教程网站上关于线性深度值的说明。  

    >首先，我们需要并不太难的 NDC 深度值转换:  
    >float z = depth * 2.0 - 1.0;  
    >然后把我们所得到的 z 值应用逆转换来检索的线性深度值:  
    >float linearDepth = (2.0 * near) / (far + near - z * (far - near));  

以上，得到的便是线性的深度值。  

## TODO  
- 自定义生成深度纹理，也就是在光源空间下的深度纹理生成。  
- Unity中Defered Rendering时，G-Buffer的排布探究。  
- 实现阴影映射（Shadow Mapping）。  

# 总结 #  
一个深度纹理竟然牵扯出这么多不知道的东西，看来做程序确实得细致阿。此外，冯乐乐大神的《Unity Shader入门精要》一书确实是解决了Unity Shader和渲染流水线之间的鸿沟。而且书中思路考虑了我等小白的思维历程，真是相见恨晚呐！  

## 参考 ##  
[1] [《Unity Shader入门精要》第四章](http://candycat1992.github.io/unity_shaders_book/unity_shaders_book_chapter_4.pdf)，介绍了数学方面相关知识。(PS:该书特别值得学习！)  
[2] [OpenGL教程中关于深度测试的一章](http://learnopengl-cn.readthedocs.io/zh/latest/04%20Advanced%20OpenGL/01%20Depth%20testing/),详细解释了什么是深度以及为什么深度是非线性的及深度可视化。  
[3] [Unity官方网站上关于DepthTexture的介绍](https://docs.unity3d.com/Manual/SL-CameraDepthTexture.html)，介绍了深度纹理的使用以及一些技巧。  
[4] [Google搜出来的Unity中深度可视化的教程](http://williamchyr.com/2013/11/unity-shaders-depth-and-normal-textures/)，从零到一的在Unity中实现深度纹理的可视化，探索思路值得学习。  
