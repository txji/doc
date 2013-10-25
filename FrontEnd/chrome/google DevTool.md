#Chrome开发者工具


##编码与开发流程

开发工作流通常涉及许多步骤用来实现一个目标。当使用开发工具进行编码的时候，可以通过优化工作流程节省时间来完成一般的任务，例如定位文件或函数、编辑脚本或样式、保存常用的代码片段或简单排列布局来更好的满足您的需求。

本节，我们将探讨一些技巧，让您的工作流在开发工具中更加高效。

###开发工具垂直分隔与水平分隔

经常使用开发工具的都知道，开发工具放置在浏览器底部时，我们可以看到更多的水平空间，与此同时，我们看到的垂直空间减少。开发工具附着到浏览器右侧，可以让检查的页面在左侧。


当在下列情景时，非常有用

* 你可能使用一个宽屏显示器,希望最大化可用空间来进行检查和调试代码。
* 你可以改变开发工具的宽度来测试调整布局。
* 垂直分隔对于调试比较长的代码时非常有用。

垂直分隔与水平分隔切换方法：

1.点击左下角Dock to main window按钮切换

![](img/chrome_docktomain.jpg)

2.拖动开发工具进行切换

![](img/devtools-drag-to-right.gif)

**注意：**开发工具会记住您最后一次选择。

###搜索、导航与过滤

####通过文件名过滤脚本、样式、代码片段

快速定位到指定的文件，对于一个开发人员来说，是至关重要的。chrome开发工具允许您搜索脚本、样式和文件片段通过下面的快捷键：

* Ctrl+o (window & linux)
* Cmd+o (mac osx)

![](img/sources_basefind.jpg)

####在当前文件中搜索文本

* Ctrl+f (window & linux)
* Cmd+f (mac osx)

![](img/sources_findone.jpg)

####在当前文件中替换文本

在搜索关键字右侧，有个Replace的checkbox，选中后，可以进行替换操作

![](img/sources_find.jpg)


####在所有文件中搜索文本

* Ctrl+shift+f (window & linux)
* Cmd+shift+f (mac osx)

![](img/sources_findall.jpg)

####通过正则表达式搜索

![](img/sources_regex.jpg)

####在一个文件中过滤一个函数或一个选择器

搜索js函数非常快，但选择器还没有试成功（有待完善）。

* Ctrl+shift+o (window & linux)
* Cmd+shift+o (mac osx)

![](img/function_filter.png)

####跳转到指定行

* Ctrl+g (window & linux)
* Cmd+g (mac osx)

![](img/sources_line.jpg)

###动态编辑脚本与样式

开发工具支持动态编辑脚本与样式，而不需要刷新整个页面。

####脚本

1.单击脚本标签选择脚本

![](img/styles_select.jpg)

2.资源tab中选择脚本

![](img/styles_sources.jpg)

具体的操作请参照javascript调试部分。

####样式

选择样式资源的方式与脚本相同，我们还可以查看一个元素的样式。

![](img/styles_inspect.jpg)

* element.style:元素style属性
* Matched css Rules:所有与该元素匹配的属性，与该元素匹配的选择器会显示为黑色，而与该元素不匹配的元素将显示为灰色，这个可以让我们很快的区分与阅读（特别是当在一堆Sprite合并在一起的时候）。


![](img/styles_hover.png)


* 创建新的样式规则
* 切换元素状态
* 颜色显示方式

####保存

![](img/saveas_saveas.jpg)


![](img/saveas_save.jpg)

###定制javascript代码片段


* 新建


![](img/snippets_new.png)

* 运行

![](img/snippets_run.png)

也可以打开代码片段后，ctrl+enter运行

##评估网络性能

网络面板是记录在应用程序中进行的每一个网络操作的信息。包括详细的计时数据、http请求与响应头、cookies、WebSocket data等。网络面板可以帮助您回答关于web应用程序网络性能方面的问题，例如：

1.first byte最慢的是哪个资源？

2.哪个资源加载（持续）时间最长？

3.谁发起了一个特殊的网络请求？

4.对于一个特殊的网络请求，在各个阶段都花费了多少时间？

###关于资源计时API

下图展示了网络数据计时点：

![](img/resource-timing-overview.png)

在chrome中，可以使用window.performance.getEntries()来获取一个数组（资源计时对象组成）。

显示某一个，window.performance.getEntries()[i]

window.performance.now()获取当前页面已经运行了多久。

###网络面板概述

当DevTools打开，网络面板会自动记录所有的网络活动。第一次打开这个面板，可能显示是空白。重新加载页面开始记录，或静静等候网络活动发生。

![](img/panel.png)

详细的字段:

![](img/field.png)

页面跳转时，保留当前网络日志：

![](img/networklog.png)

排序与筛选：

![](img/sorting.png)

时间线排序与其它的有点不同，可根据不同的时间点进行排序：


![](img/timeline-column.png)

* **Timeline:**按网络请求开始时间排序，默认排序。与sort by the start time相同。
* **Start Time:**同上
* **Response Time:**按响应时间排序。
* **End Time:**按请求结束时间排序。
* **Duration:**按请求花费的总时间排序。
* **Latency:**按请求开始到响应开始之间的时间排序，也就是常说的"Time to first byte".

按类型筛选：

![](img/filter-type.png)

添加或者移除列：

![](img/add-remove-columns.png)

改变行的尺寸：

![](img/changeRowSize.png)

时间线视图：

第个资源的加载时间显示为时间条，浅色部分为延时时间（也就是请求开始到响应开始的时间，即First Byte时间），深色部分为接收数据时间。

![](img/network-timeline.png)

当鼠标放在时间线单元格（但不在时间条上）中时，就会显示**延迟时间**与**接收数据时间**

![](img/timeline-view-1.png)

如果放在时间条上，将会显示一个浮层

![](img/timeline-view-hover.png)


**DOMContentLoaded Event & Load Event**

![](img/dom-lines.png)


时间线颜色

![](img/Timeline-color.png)

保存与复制网络信息

右键：

![](img/right-click.png)

有些是针对选中资源的：

![](img/sources_selected.png)

保存网络数据：

HAR数据

![](img/har.png)

关于har数据的查看请看下面的文章：<http://www.igvita.com/2012/08/28/web-performance-power-tool-http-archive-har/>

###网络资源详情

http响应头

![](img/headers.png)

资源预览(不同资源预览效果不同)

![](img/resource-preview-json.png)

![](img/image-preview.png)

http响应

![](img/response.png)

Cookies

![](img/cookies.png)