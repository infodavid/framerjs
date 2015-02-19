
# Framerjs 中文文档 - 03

## 状态

`状态`允许你定义一个图层的多个表现。当创建一个图层的时候，，你定义的一些列属性就成为你的`默认状态`。一个图层可能有多个状态，每一个都有一系列不同的属性。状态可以循环，拥有或者没有动效。<!--more-->

### 添加状态

`layerA`的默认状态包括了值为1的透明度属性，接下俩，定义了`layerA`的一个新状态，名为`fade`，透明度为0。

	# 默认状态
	layerA = new Layer 
	    opacity:1
	
	# 新的名为 fade 的状态
	layerA.states.add
	    fade: {opacity:0}
	    
`layerA`若要继承`fade`状态的属性，它需要从默认状态转换到`fade`状态。

	# 通过动效切换状态
	layerA.states.switch("fade")
	
	# 无动效切换状态
	layerA.states.switchInstant("fade")
	
### 案例

`状态`之间同样可以被触发，通过使用 `next()`代替`switch()`。

	# 添加状态
	layerA.states.add 
	    second: {scale:0.75} 
	    third:  {rotation:90, scale:1} 
	
	# 设置动画选项
	layerA.states.animationOptions = 
	    curve: "spring(600,30,0)"
	
	# 点击时触发状态
	layerA.on Events.Click, -> 
	    layerA.states.next()
	    
和图层动效一样，状态动效的动效曲线和时间都可以被定义。一个图层所有状态的`animationOptions`都可以立即定义，正如上图的案例展示的一样。

### 编辑状态

你可以移除或者复写之前定义的状态。复写状态的话，只需要用同一个名称简单的添加一个新状态即可。

	# 移除第二个状态
	layerA.states.remove("second")
	
	# 复写第三个状态
	layerA.states.add
	    third: {blur:10}
	    
## 总结

- 状态是一系列的属性

- 每一个图层都有一个默认的状态

- 你可以在状态间进行动效处理

- 状态可以被移除或者复写









