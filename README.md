# header头部信息
——
每当我们开发维护一个项目时候，会把一些通用的代码直接复制粘贴过来使用，但其实不懂它的作用，或许它减少了我们很多工作量，但或许他是一颗定时炸弹，会炸很多坑而找不到其根源。今天，我们从Html头信息来切入，讲解一些比较常见通用的头信息。

在我们项目里有这么一段：

```
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no, minimal-ui"><meta name="screen-orientation" content="portrait"/>
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="format-detection" content="telephone=no">
<meta name="full-screen" content="yes">
<meta name="x5-fullscreen" content="true">
```
我们来一段段拆解~

首先了解下什么是meta:
> <meta> 元素可提供有关页面的元信息（meta-information），比如针对搜索引擎和更新频度的描述和关键词。

> <meta> 标签位于文档的头部，不包含任何内容。<meta> 标签的属性定义了与文档相关联的名称/值对

并且：
> 注释：<meta> 标签永远位于 head 元素内部。
元数据总是以名称/值的形式被成对传递的。

接下来我们解读下现有项目的meta信息：

(1) charset

charset是规定 HTML 文档的字符编码：一般设置为UTF-8（UTF-8   [8-bit Unicode Transformation Format]）是一种针对Unicode的可变长度字符编码，又称万国码。

也有很多网站为国标字体但是因为浏览器的兼容性问题，可能显示乱码，很不友好。

(2) viewport

手机浏览器是把页面放在一个虚拟的“窗口”（viewport）中，通常这个虚拟的“窗口”（viewport）比屏幕宽，这样就不用把每个网页挤到很小的窗口中（这样会破坏没有针对手机浏览器优化的网页的布局），用户可以通过平移和缩放来看网页的不同部分。移动版的 Safari 浏览器最新引进了 viewport 这个 meta tag，让网页开发者来控制 viewport 的大小和缩放，其他手机浏览器也基本支持。



width=device-width：宽度设置为屏幕宽度。
initial-scale=1.0：缩放比例为1，也就是不缩放。
maximum-scale=1.0：最大缩放比1。
minimum-scale=1.0：最小缩放比1，与前者这么看来的话，就是不让用户缩放喽。
user-scalable：用户是否可以手动缩放，否。
minimal-ui：让网页在加载时便可隐藏顶部的地址栏与底部的导航栏。

(3) screen-orientation

屏幕锁定方向：unspecified（默认）、portrait（纵向）、landscape（横向）、sensor（传感器方向）

(4) apple-mobile-web-app-capable

这meta的作用就是删除默认的苹果工具栏和菜单栏。

content有两个值”yes”和”no”,当我们需要显示工具栏和菜单栏时，这个行meta就不用加了，默认就是显示。

(5) format-detection

format-detection翻译成中文的意思是“格式检测”，顾名思义，它是用来检测html里的一些格式的，那关于meta的format-detection属性主要是有以下几个设置：
meta name="format-detection" content="telephone=no"
meta name="format-detection" content="email=no"
meta name="format-detection" content="adress=no" 
也可以连写：meta name="format-detection" content="telephone=no,email=no,adress=no"

在移动端手机默认会把某些格式当做链接，例如：「13344443333」会被默认为电话号码，「kakaka@lala.haha」呗默认为邮箱地址，「39.6733507988,116.6747761032」被视为经纬度。

如果我们不想将它进行转换可以添加这个属性都为NO。

(6) full-screen

顾名思义就是全屏模式，Yes。

(7) x5-fullscreen

QQ、微信强制全屏。

拓展几个meta知识：
(1)  apple-touch-icon

如果 apple-mobile-web-app-capable 设置为 yes 了，那么在苹果机的safari上可以通过添加到主屏按钮将网站添加到主屏幕上。而设置相应 apple-touch-icon 标签，则添加到主屏上的图标就会使用我们指定的图片。

(2) apple-touch-startup-image

基于 apple-mobile-web-app-capable 设置为 yes ，可以为WebApp设置一个类似NativeApp的启动画面。和 apple-touch-icon 不同， apple-mobile-web-app-capable 不支持sizes属性，要使用media来加载不同的启动画面，也就是说从主屏幕打开时有个加载图片。

(3) viewpoint-fit

所以引入了一个 meta 标签的 viewpoint 扩展属性——viewpoint-fit，在 iOS 11 中 viewpoint-fit 也官方添加到 CSS Round Display 规范中了。

通过 viewport-fit 可以设置可视视窗的大小，它有三个属性值：

Auto：默认值。这个值不影响初始布局视窗，整个 Web 页面是可视的。

Contain：最初的布局视窗和视觉布局视窗被设置为最大的矩形。

Cover：初始布局视窗和视觉布局视窗被设置为设备物理屏幕的限定矩形。

所以我们可以在X上设置Cover。
(4) keywords

"keywords" 是一个经常被用到的名称。它为文档定义了一组关键字。某些搜索引擎在遇到这些关键字时，会用这些关键字对文档进行分类。
(5)  description

网页简短描述不能太长，应该保持在140-200个字符或者100个左右的汉字；

不要给网页定义与网页描述内容无关的简短描述；

由于网页制作者滥用description(提供与网页无关的简短描述)，导致目前常用的搜索引擎降低了description的重要性

(6)  robots 

属性值 -- 定义网页搜索引擎索引方式，robots用于定义网页搜索引擎索引方式

robots出现在name属性中，使用content属性定义网页搜索引擎索引方式

通过使用meta的robots属性值可以为没有文件上传权限的用户提供/robots.txt文件的所有功能

--------------------------------------------------------------------------------------------------------------

参考文章网址：

W3C中文网

http://caibaojian.com/mobile-meta.html

