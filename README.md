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


## Basic usage ##

Create a placeholder div to put the graph in:

```html
<div id="placeholder"></div>
```

You need to set the width and height of this div, otherwise the plot
library doesn't know how to scale the graph. You can do it inline like
this:

```html
<div id="placeholder" style="width:600px;height:300px"></div>
```

You can also do it with an external stylesheet. Make sure that the
placeholder isn't within something with a display:none CSS property -
in that case, Flot has trouble measuring label dimensions which
results in garbled looks and might have trouble measuring the
placeholder dimensions which is fatal (it'll throw an exception).

Then when the div is ready in the DOM, which is usually on document
ready, run the plot function:

```js
$.plot($("#placeholder"), data, options);
```

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


## Notes about the examples ##

In order to have a useful, functional example of time-series plots using time
zones, date.js from [timezone-js][timezone-js] (released under the Apache 2.0
license) and the [Olson][olson] time zone database (released to the public
domain) have been included in the examples directory.  They are used in
examples/axes-time-zones/index.html.


[excanvas]: http://code.google.com/p/explorercanvas/
[flashcanvas]: http://code.google.com/p/flashcanvas/
[timezone-js]: https://github.com/mde/timezone-js
[olson]: ftp://ftp.iana.org/tz/
