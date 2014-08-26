# Framer.js 中文翻译版

## 图层

一个图层就是浏览器里画材料的矩形。它有一些基础的属性设置，比如说 x, y 宽和高，同事还有一些其他的属性，比如说透明，缩放，以及模糊。图层可以显示图片，文本，或者两者结合。

    # 这样创建了一个新图层，秉着设置她的 x 属性到100
    myLayer = new Layer({x:0, y:0, width:128, height:128})
    myLayer.x = 100

## 继承

图层可以被其他图层包含，我们把这种图层叫 `子图层`。这个图层的父类被称为 `父图层`。图层继承他们的父图层，举个例子，如果你设置一个图层的透明度到0.5，所有的子图层都会拥有一个0.5的透明度。

一个图层的坐标是基于它的父图层的。如果 x 和 y 都是0，一个图层将会位于它的父图层的左上角。如果你需要的话，你可以操控图层的继承。

    # 给一个图层添加一个子图层
    parentLayer.addSublayer(childLayer)
## 图片和滚动
大部分的图层就只包含一个图片，通过图片属性可以轻松的进行设置。

    # 设置一个图片
    layer = new Layer({width:100, height:100, image:”my-image.png})

图层同样可以滚动他们的内容。你可以用滚动关键词开启滚动。

    # 让图层可滚动
    layer = new Layer({width:100, height:100})
    layer.scroll = true

创建一个项目间可复用的由多个图层组成的组件也是很容易的。一个包含不同图层的有特定任务的组件被叫做一个`“视图 View” `（其他的名字叫组件或者部件）。一些在 iOS 上的视图叫表格视图，集合视图等等。

## 动画

一个图层的大多数属性都可以动画：x, y, 宽度，高度，缩放，透明度等等。你可以同时让多个属性动画。
动画可以选择一种描述动画类型的曲线。你可以使用一些预先定义好的曲线比如说 `线性` 或者 `渐入` ，一些常用的或者弹出动画。

你可以明确的创建一个动画，运用 `myAnimation = layer.animate({..})`或者用简写 `layer.animate({..})`

    # 创建一个弹出动画
    springUp = layer.animate(
      properties: {y: layer.y + 100}
      curve:”spring(100,10,0)”,
    })

## 样式化

因为 Framer 运行在浏览器中，所以你可以简单地使用 html 和 css 去样式化任何图层。设置一个图层的 html 内容可以使用 `somelayer.html = “hello”`。你可以设置文本或者html.

要添加 CSS 样式，你可以编辑图层样式特性的属性，你可以一次性设置这些，像是 `layer.style.backgroundColor = “red” `或者`layer.style['background-color'] = “red”`，也可以像下面这个例子一样一次性更新多个属性。需要注意的是，虽然大部分 framer 属性可取数值，但样式特性仍需要特定的 css 值。如`layer.style.lineHeight = “16px”`，你也可以通过 `layer.classList.add(“myClass”)` 来设置一个 css；这样，你就可以使用一个外部的css文件进行样式化。

  # 一次设置多个图层样式
  layer.style = {"font-size": "18px","text-align": "center",
  "line-height": "24px","color": "red"}

备注：如果你在一个图层中设置单个样式，别忘了使用 JavaScript 的语法，比如说 ‘font-size’ 就会是 layer.fontSize

## 事件

事件是指可能发生在图层的事情，例如用户点击或者鼠标悬停，或者是滚动。你可以监听这些事件并响应它们去构建简单（或复杂的）交互。
你可以监听很多的事件，但是最有趣的可能是单击，双击，悬停，鼠标移出，以及按下按键。移动浏览器有一些特定的触摸事件：触摸开始，触摸移动以及触摸结束。

Framer 有一个辅助方法可以很好的为你匹配大多数的事件，比如说 `Events.TouchStart` 在电脑里会被称为“鼠标按下”，在移动设备中会被叫做“触摸开始”。

要监听一个时间的话，使用 `layer.on event, ->…` 停止监听的话，可以使用 `layer.off event, -> …` 你可以一次监听多个事件
  
  # 在一个图层中监听多个事件
  layer.on Events.TouchStart, (event) ->
  console.log "Touch/click start happened on layer"layer.on Events.TouchMove, (event) -> 
  console.log "Touch/click is moving!"layer.on Events.TouchEnd, (event) ->
  console.log "The touch has ended :("

你会注意到函数中的 `event`，它是一个拥有附加信息（有关事件发生的，比如说位置信息）的对象。

## 状态机

状态机是 Framer3 中的一个新功能，这个功能强大的令人震惊，而且很有用。它允许你对一个图层添加多个状态。可以把一个状态当做一组用语图层的有单个或多个属性。图层可以有多个状态，你可以添加和删除它们，并且可以对状态之间进行切换或者动画处理。所有图层的状态可以有同样的动画属性，比如说动画曲线。你随时都可以访问图层的任何一个状态。图层同样拥有一个“默认”的状态，就是图层创建时间的属性。

当一个图层需要在屏幕上的时候，但是在不同的位置或者大小等等时，状态是最有用的。比如说，我们用了状态机来对图层添加三种状态，然后在点击它们时进行动画切换。
