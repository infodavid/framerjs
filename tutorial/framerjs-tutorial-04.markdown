

# Framerjs 中文文档 - 04

## 事件

事件指的是可以发生在一个图层上的事情，大多数被用户的交互行为处罚。用事件的话，你可以基于这些交互来动效化图层。Framer 包含了非常多的事件，如：`点击事件`, `触摸事件`，`滚动事件`，`拖拽事件`等等。<!--more-->

要监听一个事件的话，使用 `layer.on event, ->…` 

停止监听的话，可以使用 `layer.off event, -> …`

### 监听多个事件

	layerA.on Events.Click, -> 
	    ...
	layerA.on Events.TouchStart, -> 
	    ...
	layerA.on Events.TouchMove, -> 
	    ...
	layerA.on Events.TouchEnd, -> 
	    ...
	    
大多数情况下可用的一个处理为通过点击处罚一系列状态间的开关。

	# 通过点击打开状态
	layerA.on Events.Click, -> 
	    imageLayer.states.next()
	    
### 案例

事件可以用来衔接动效。用这些事件，你可以通过监听`动效结束（AnimationEnd）`事件，在一个动效结束后，开始一个新的动效。

	# Animation Events
	layerA.on Events.AnimationStart, ->
	    ...
	layerA.on Events.AnimationEnd, ->
	    ...
	    
下面就是一个简单的衔接动效的案例。每一个动效都获得一个`动效结束（AnimationEnd）`事件，这样他们就可以无限衔接。

## 总结

- 事件就是可以发生的一个图层上的事情

- 事件经常用来转换状态

- 动效可以通过`动效结束（AnimationEnd）`事件进行衔接

