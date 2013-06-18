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

这里，data是data series的一个数组
Here, data is an array of data series and options is an object with
settings if you want to customize the plot. Take a look at the
examples for some ideas of what to put in or look at the 
[API reference](API.md). Here's a quick example that'll draw a line 
from (0, 0) to (1, 1):

```js
$.plot($("#placeholder"), [ [[0, 0], [1, 1]] ], { yaxis: { max: 1 } });
```

The plot function immediately draws the chart and then returns a plot
object with a couple of methods.


## What's with the name? ##

First: it's pronounced with a short o, like "plot". Not like "flawed".

So "Flot" rhymes with "plot".

And if you look up "flot" in a Danish-to-English dictionary, some of
the words that come up are "good-looking", "attractive", "stylish",
"smart", "impressive", "extravagant". One of the main goals with Flot
is pretty looks.


## 示例说明 ##

为了展示一个有用的时序图示例功能，使用了时区，引用[timezone-js][timezone-js]（Apache 2许可证发布）中date.js文件
和[Olson][olson]奥尔森时区数据库都已包含在实例目录。我们在示例“examples/axes-time-zones/index.html”使用了。


[excanvas]: http://code.google.com/p/explorercanvas/
[flashcanvas]: http://code.google.com/p/flashcanvas/
[timezone-js]: https://github.com/mde/timezone-js
[olson]: ftp://ftp.iana.org/tz/
