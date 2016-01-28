# MyLayerTest

一张复杂的画可以有很多的图层叠加起来，形成一个复杂的图像。在Android中，使用saveLayer()方法来创建一个图层，图层同样是基于栈的结构进行管理的，Android通过调用saveLayer，saveLayerAlpha方法将一个图层入栈，使用restore，restoreToCount方法将一个图层出栈。入栈的时候，后面所有操作都发生在这个图层上，而出栈的时候，则会把图像绘制到上层canvas上。

仿照API Demos里面的示例，学习如何使用Layer,代码如下

canvas.drawColor(Color.WHITE); 
mPaint.setColor(Color.BLUE); 
canvas.drawCircle(150, 150, 100, mPaint); 
canvas.saveLayerAlpha(0, 0, 400, 400, 255, LAYER_FLAGS); 
mPaint.setColor(Color.RED); 
canvas.drawCircle(200, 200, 100, mPaint); 
canvas.restore(); 



Canvas.saveLayerAlpha(float left, float top, float right, float bottom, int alpha, int saveFlags)：
分配了一个画布用于绘制图层。它定义了一个画布区域（可设置透明度），此方法之后的所有绘制都在此区域中绘制，直到调用canvas.restore()方法。例如：在调用saveLayerAlpha方法之前绘制了一个“圆形”，在调用saveLayerAlpha方法之后绘制了一个“圆形”此时这两个圆形并不在同一个图层。

在onDraw方法中绘制两个相交的圆，这两个圆位于不同的图层。然后将后面图层的透明度设置我0~255不同数值

当透明度设置为0,即完全透明时

![](http://github.com/946898963/MyLayerTest/raw/master/fulutupian/0.png)

当透明度设置位127，即透明时

![](http://github.com/946898963/MyLayerTest/raw/master/fulutupian/127.png)

当透明度设置为255,即完全不透明时

![](http://github.com/946898963/MyLayerTest/raw/master/fulutupian/255.png) 
