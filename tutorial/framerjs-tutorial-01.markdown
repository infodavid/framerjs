
# Framerjs 中文文档 01

## 图层

`图层`是一个可以绘制元素的矩形。`图层`可以显示图像，视频和文本。每一个图层都继承了一系列的默认属性：宽度、高度、以及一个蓝色背景。


	# 创建一个图层					   
	layerA = new Layer 	   
		x:0, y:0, width:0, height:100 
		
(注：在未指定背景颜色的情况下，默认背景颜色为蓝色)

### 属性

一个图层的位置，大小尺寸，以及样子都是被它的属性所定义的。除了可以定义一个图片，背景，或者视频，也同样可以转换、隐藏、缩放等等。

	layerB = new Layer
	    backgroundColor:"#2DD7AA",
	    width:60, height:60,
	    scale:1, borderRadius:3
	    
同时在创建图层后后，你也可以定义和复写图层的属性。

	layerB.borderRadius = 3
	layerB.rotation = 45
	layerB.opacity = 0.8
	layerB.scale = 0.8

### 定位

一个图层可以被它的 x 和 y 属性定位。这些值定义了与画布左上角的距离。`注：左上角的起始位置为(0,0)。` `minX`, `minY`, `midX`, `midY`, `maxX` 和 `maxY`等值同样可以用于定位一个图层。

	# 图层 A 的属性
	# x:40, y:40, width:80
	layerB.x = layerA.x     # 40
	layerB.x = layerA.minX  # 40
	layerB.x = layerA.maxX  # 120
	
画布的左上角到图层的中心位置可以通过 `midX` 和 `midY` 计算得出。

	# 中心点的 x 值
	layerB.x = layerA.midX  # 80
	
	# 中心点的 Y 值
	layerB.y = layerA.midY  # 80
	
你可以让一个图层在它的父图层中居中（详见`继承`），或者是通过调用 `center()` 函数，在屏幕中居中。图层同样可以水平或垂直居中。

	# Center
	layerA.center()
	
	# Center horizontally
	layerA.centerX()
	
	# Center vertically
	layerA.centerY()
		
### 继承

图层可以包含`图片`，`视频`和`文本`。

## 总结

- 图层可以被属性定义

- 图层层级关系，同时从父元素中继承属性

- 图层可以被转换，缩放，遮罩，旋转等等。

- 图层可包含图片，视频和文本。





