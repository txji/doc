#使用 aria-haspopup 在支持触摸的设备上模拟悬停

##概述

在一个网页元素上悬停光标是使用鼠标和键盘浏览时的一个常见操作，但进行基于触摸的浏览器却没有对应的操作。Windows 8 中的 Internet Explorer 10 引入了 **aria-haspopup** 文档对象模型 (DOM) 属性的新用法：在支持触摸的设备上模拟悬停。

标题范围有点大，称它为标题党一点也不为过。但增强用户体验上，确实还是不错的。

**注意：此行为不适应于windows 7中的IE10**

网页上的常见模式是隐藏鼠标悬停后的交互式内容。例如，用户可以使用鼠标指向一个元素，并在其下显示一个菜单。悬停通常通过使用 :hover  级联样式表 (CSS) 伪类或者 onmouseover  DOM 事件启用。

Internet Explorer 10 向现有 aria-haspopup 属性添加新的行为，以模拟具有隐藏交互式内容的页面元素上的悬停。

在一个页面元素上（例如菜单），将元素的 aria-haspopup 属性设置为 "true"。当支持触摸的设备上的 Internet Explorer 10 用户第一次点击页面元素时，用户的体验与将光标悬停在该元素上的用户的体验相同。在用户点击页面上的其他位置、再次点击该元素或导航到其他页面前，该元素保留其悬停状态。此外，onclick 事件的默认操作（指浏览器默认行为，而不是onclick事件。例如链接的导航）不在第一次点击页面元素时执行。


CSS

	<style>
		.demo{float:left;width:200px;height:200px;background-color:red;position:relative;z-index:1;margin-right:10px;}
		.demo-in{display:none;width:50px;height:50px;position:absolute;z-index:1;right:0;bottom:0;background-color:green;}
		.demo:hover .demo-in{display:block;}
	</style>

HTML

	<a class="demo" href="http://www.ctrip.com" onclick="alert(1);">
		携程旅行网
		<span class="demo-in">
		</span>
	</a>
	
	<a class="demo" href="http://www.ctrip.com" aria-haspopup="true" onclick="alert(2);">
		携程旅行网
		<span class="demo-in">
		</span>
	</a>