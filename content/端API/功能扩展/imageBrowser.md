/*
Title: imageBrowser
Description: imageBrowser
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

#**概述**

imageBrowser模仿系统相册，实现了对本地以及网络图片的查看浏览。可以是九宫格方式也可以是图片流方式，效果流畅

![图片说明](/img/docImage/imageBrowser.jpg)

#**openImages**

打开图片浏览器

openImage({params})

##params

imageUrls：

- 类型：数组
- 默认值：无
- 描述：图片的url（支持的路径协议：widget://,fs://,http://,https://）组成的数组，不可为空

showList：

- 类型：布尔
- 默认值：true
- 描述：是否以九宫格方式显示图片

activeIndex：

- 类型：数字
- 默认值：0
- 描述：当不用九宫格方式显示时，当前要显示的图片在集合中的索引

##示例代码

```js
var obj = api.require('imageBrowser');
obj.openImages({
	imageUrls: ['fs://a.png','fs://b.png'],
	showList:true,
	activeIndex:2
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
