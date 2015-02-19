# Framerjs 中文文档 - 02

## 动效

图层的属性可以动效化的，包括`x`, `y`, `width`, `height`, `scale`, `opcity`,` rotation`等等。并且可以一次动画处理多个属性。

	layerA.animate
	    properties:
	        opacity: 0.5

### 时长
	        
除了在使用`弹性曲线`动画时不行，其他时候都可以定义一个动画的时长。动效同样可以被延迟和重复。在 Framer 里所有的时长都是以秒来定义的。

	layerA.animate
	    properties:
	        opacity: 0.5
	    curve: "ease"
	    repeat: 1
	    delay: 2
	    time: 1
	    
### 曲线

你可以选择一个描述动效类型的曲线的动效。你可以使用一些预先定义好的曲线比如说`线性`，或者`渐入`,定制的`贝塞尔曲线`和`弹性动画`。以下是一些总览图。

## 总结

- 可以一次动效化多个属性

- 动画可以设置时间，延迟，以及重复。

- Framer 包含了多种动效曲线，包括`弹性动画`

