---
layout: post
title:  "Unity中MRT（Multi Render Target）的实现"
date:   2017-12-06
tag:
- [Unity Shader]
comments: true
---

在学习图像大佬龚敏敏的KlayGE以及在看OpenGL书籍时，就接触到了MRT的概念。在KlayGE中，主要用处是将法线、位置、颜色等信息存储在一张纹理中，然后进行延迟渲染。延迟渲染可以很好得解决多灯光的场景渲染效率低的问题，虽然目前并没有看懂延迟渲染的实现...

### Unity中MRT的实现

Unity中提供了许多方便的接口，但是经常是文档描述不清楚或者说水平有限，导致很多方法并没有搞懂什么意思。前几天逛Github时，看到有个哥们实现了一下MRT，和OpenGL中的处理其实是一样的。

 ### 1. 首先创建一系列需要的帧缓存，对应到OpenGL中就是FrameBuffer，代码如下。
 
 {% highlight c# %}
this.rts = new RenderTexture[4] {
    new RenderTexture(sourceCamera.pixelWidth, sourceCamera.pixelHeight, 0, RenderTextureFormat.Default),
    new RenderTexture(sourceCamera.pixelWidth, sourceCamera.pixelHeight, 0, RenderTextureFormat.Default),
    new RenderTexture(sourceCamera.pixelWidth, sourceCamera.pixelHeight, 0, RenderTextureFormat.Default),
        new RenderTexture(sourceCamera.pixelWidth, sourceCamera.pixelHeight, 0, RenderTextureFormat.Default)
    };
    rts[0].Create();
    rts[1].Create();
    rts[2].Create();
    rts[3].Create();
{% endhighlight %}

### 2. 给FrameBuffer挂上RenderBuffer。帧缓存对象就是一个容器，上边必须要挂RenderBuffer，或者可选择得创建深度渲染。Unity中代码如下。

 {% highlight c# %}
 this.colorBuffers = new RenderBuffer[4] { rts[0].colorBuffer, rts[1].colorBuffer, rts[2].colorBuffer, rts[3].colorBuffer };
{% endhighlight %}

### 3.然后就是需要注意摄像机的一些API，官方文档这部分倒描述的差强人意。

 {% highlight c# %}
this.sourceCamera = this.GetComponent<Camera>();
tempCamera = new GameObject().AddComponent<Camera>();
tempCamera.enabled = false;
void OnRenderImage(RenderTexture source, RenderTexture destination)
{
    tempCamera.CopyFrom(sourceCamera);
    tempCamera.SetTargetBuffers(this.colorBuffers, this.depthBuffer.depthBuffer);
    tempCamera.cullingMask = 1 << LayerMask.NameToLayer("Lerpz");
    tempCamera.RenderWithShader(MRTShader, "");
    Graphics.Blit(rts[rt.GetHashCode()], destination);  
}
{% endhighlight %}

### 4. 最后就是DX的Shader中有一个语义的概念，其中SV_Target可以控制输出到哪个帧缓存中。

{% highlight c# %}
struct fout 
{
    float4 rt0 : SV_Target0;
    float4 rt1 : SV_Target1;
    float4 rt2 : SV_Target2;
    float4 rt3 : SV_Target3;                
};
fout frag(v2f i)
{
    float depth = i.pos.z / i.pos.w;
    fout o;
    o.rt0 = float4(depth, depth, depth, 1);
    o.rt1 = _Color;
    o.rt2 = float4(i.normal.xyz, 1);
    o.rt3 = float4(i.worldNormal.xyz, 1);
    return o;
}
{% endhighlight %}

