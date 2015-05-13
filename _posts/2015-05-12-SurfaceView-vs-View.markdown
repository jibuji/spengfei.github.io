---
layout: post
title:  "android中SurfaceView与View的绘制性能对比"
date:   2015-05-12 14:29:34
categories: technology
---

#android中SurfaceView与View的绘制性能对比
先比较下两种使用的方法：
1. SurfaceView的惯用法：
{% highlight java %}
SurfaceHolder holder = mSurfaceView.getHolder();
//这里的canvas是android.graphics.Canvas
Canvas canvas = holder.lockCanvas();
//do some drawing stuff here
holder.unlockCanvasAndPost();
{% endhighlight %}

2. View的惯用法：
为了能直接控制绘制的逻辑，我们通常会继承View，覆盖onDraw方法：
{% highlight java %}
class MyView extends View {
    /**在打开了硬件加速的情况下，这里的canvas是android.view.GLES20Canvas,
     * 否则是android.graphics.Canvas
    */
    protected void onDraw(Canvas c) {
        //do some drawing stuff here.
    }
}
{% endhighlight %}

经实验发现：**GLES20Canvas的性能明显高于Canvas**。也就是说:
*在打开硬件加速的情况下，方法2的绘制性能明显高于方法1。*
*但在关闭硬件加速的情况下，这两个方法的性能相当，但由于方法1可以使得绘制放在另外一个线程，不会阻塞主线程，从这个角度来看，方法1优于方法2。*


具体实验的代码工程请参见<https://github.com/spengfei/android-surfaceview-vs-view>
