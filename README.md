# Flot [![Build status](https://travis-ci.org/flot/flot.png)](https://travis-ci.org/flot/flot)


##关于##

Flot是一款基于jquery的图表绘制Javascript类库。     
请到官网了解更多：<http://www.flotcharts.org/>。

##使用##

在引入jQuery文件后引入该类库Javascript文件即可。  
所有支持HTML5 canvas标签的浏览器都支持该控件。  
为了让低版本（IE<9）支持,使用[Excanvas],一个canvas模拟器，可以让IE支持canvas; 你只需如下引入excanvas脚本文件即可:

```html
<!--[if lte IE 8]><script language="javascript" type="text/javascript" src="excanvas.min.js"></script><![endif]-->
```

如果在IE6上没有工作，检查是否支持VML，excanvas使得IE能通过VML支持Canvas标签。当在
在不支持VML的虚拟机上的测试环境的精简版本会出现上述情况。



You can also try using [Flashcanvas][flashcanvas], which uses Flash to
do the emulation. Although Flash can be a bit slower to load than VML,
if you've got a lot of points, the Flash version can be much faster
overall. Flot contains some wrapper code for activating Excanvas which
Flashcanvas is compatible with.

You need at least jQuery 1.2.6, but try at least 1.3.2 for interactive
charts because of performance improvements in event handling.


## 基本语法 ##

创建id为placeholder的div来放入图表：

```html
<div id="placeholder"></div>
```

你需要设置div的宽和高，否则plot类库将不知道图表的如何缩放。你可以像下面使用内联方式设置width、height：

```html
<div id="placeholder" style="width:600px;height:300px"></div>
```

你也可以使用外部样式。要确保placeholder的div标签不包含在CSS属性为display:none的元素中。
这样Flot测量标签的大小存在问题导致图像混乱；同样测量placeholder的div元素的存在问题将是致命的(将会抛出异常)。  

当div在DOM中创建成功，文档也加载好了，运行plot的初始化函数：

```js
$.plot($("#placeholder"), data, options);
```

这里，data是data series的一个数组.options是一个设置参数的集合，我们可以设置该集合的值来实现定制化。
下面我们看些示例或者到[API reference](API.md)。下面我们将在点(0, 0)和 (1, 1)之间画一条直线:

```js
$.plot($("#placeholder"), [ [[0, 0], [1, 1]] ], { yaxis: { max: 1 } });
```

plot函数立即画出图表，返回包含一些方法的plot对象。


## Flot命名 ##

flot 跟plot发音相似  /plɒt/。 
flot在丹麦语中意为“漂亮的”、“时髦的”、“吸引人的”、“令人着迷的”。  
Flot的最重要的目标之一就是看起来十分漂亮。


## 示例说明 ##

为了展示一个有用的时序图示例功能，使用了时区，引用[timezone-js][timezone-js]（Apache 2许可证发布）中date.js文件
和[Olson][olson]奥尔森时区数据库都已包含在实例目录。我们在示例“examples/axes-time-zones/index.html”使用了。


[excanvas]: http://code.google.com/p/explorercanvas/
[flashcanvas]: http://code.google.com/p/flashcanvas/
[timezone-js]: https://github.com/mde/timezone-js
[olson]: ftp://ftp.iana.org/tz/
