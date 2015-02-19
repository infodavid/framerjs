
# Framerjs 中文文档 - 06

## 滚动

图层只要包含了一个超过它高度或宽度的`子图层`，就可以被滚动。<!--more-->

	# 父图层
	layerA = new Layer 
	    height:100
	
	# 子图层
	layerB = new Layer 
	    height:200, superLayer:layerA
	
	# 在父图层启用滚动
	layerA.scroll = true
	
图层同样可以设置为只能水平或垂直滚动。

	layerA.scrollHorizontal = true
	layerA.scrollVertical = true
	
Framer 同样包含一个滚动事件。在滚动事件作用下，可滚动图层的位置可以被获取到。图层动效可以基于这些位置，通过条件语句触发。

	# 滚动事件
	layerA.on Events.Scroll, ->
	    print layerA.scrollX
	    print layerA.scrollY
	    
## 总结

- 图层若包含一个更大的子图层，可以被滚动。

- 你可以指定滚动的朝向

- 图层动效可以通过滚动触发
