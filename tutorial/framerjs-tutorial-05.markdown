
# Framerjs 中文文档 - 05

## 拖拽

要创建一个可拖拽的图层的话，非常简单，只需要设置`draggable.enabled`为`true`就可以了。你同样可以指定拖动的速度。如果你只想水平或者垂直拖动一个图层的话，下面这个方面非常有用：设置`speedX`或者是 `speedY`为0。设置值大于1，可以创建加速的拖动。<!--more-->

	# 让图层可拖拽
	layerA.draggable.enabled = true
	
	# 设置拖动速度
	layerA.draggable.speedX = 1
	
	# 阻止垂直拖动，让其只能水平拖动
	layerA.draggable.speedY = 0
	
Framer 有三个你可以监听的拖拽事件：`DragStart`,`DragMove`以及`DragEnd`。

	# 开始拖动
	layerA.on Events.DragStart, -> ...
	
	# 正在移动克此可拖拽图层的时候
	layerA.on Events.DragMove, -> ...
	
	# 拖拽后
	layerA.on Events.DragEnd, -> ...
	
### 案例

下面，拖拽事件用来制作一个简单的交互。

首先，图层的当前的 X 和 Y位置被保存在变量中。当我们放开图层时，`拖拽结束`事件就会被触发，然后图层会弹回到原来的位置。

	originX = layerA.x
	originY = layerA.y
	
	layerA.on Events.DragEnd, ->
	    layerA.animate
	        properties:
	            x: originX, y: originY
	        curve: "spring(600, 30, 0)"
	        
## 总结

- 设置`draggable.enabled`为`true`就可以创建可拖拽的图层

- 拖拽的方向可以被`speedX` 和 `speedY`定义

- 图层有三个拖拽事件： `DragStart`,`DragMove`以及`DragEnd`



