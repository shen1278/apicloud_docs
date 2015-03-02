/*
Title: tabBarMenu
Description: tabBarMenu
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[setBarSelect](#3)

[setBadge](#4)

[removeBadge](#5)

[hide](#6)

[show](#7)

[hideMenu](#8)

[showMenu](#9)
</div>

#**概述**

tabBarMenu生成一个应用底部导航菜单模块，类似qq空间的底部导航菜单，开发者可自定义菜单各种样式

![图片说明](/img/docImage/tabBarMenu.jpg)

#**open**<div id="1"></div>

打开
open({params}, callback(ret, err))

##params

defaultBarSelect:

- 类型: 数字
- 默认值: 0
- 描述：默认选中的标签栏按钮.可为空

autoLayout: 

- 类型: 布尔值.
- 默认值: true
- 描述: 是否自动智能调整当前页面webView的位置: 使其距离屏幕底部距离变为 49.可为空

barItems：

- 类型：数组
- 默认值：无
- 描述：标签栏各按钮信息

内部字段:

```js
[{
	title:			//标题.
	bgImg: 			//背景图路径.
	bgImgClick: 	//被点击后的背景图路径.
}]
```

barItemConfig：

- 类型: JSON对象
- 默认值：无
- 描述：标签栏各按钮的配置

内部字段:

```js
{
	titleColor: 		//文本颜色,默认“#ffffff”(白色),格式为#fff、#ffffff、rgba(r,g,b,a).
	titleSelectColor:	//选中状态时,按钮文本的颜色,默认“#ffffff”(白色).
	fontSize: 			//文字尺寸默认11.0
	textMarginTop: 		//文本距离按钮上边界的距离,默认41.0
	primaryItem: 		//点击会弹出菜单的按钮的下标, 默认 2(即第三个按钮)
}
```

barConfig：

- 类型：JSON对象
- 默认值：无
- 描述：标签栏配置

内部字段:

```js
{
	bgImg: 		//背景图片路径.
}
```

menuItems：

- 类型：数组
- 默认值：无
- 描述：菜单各菜单项的信息

内部字段：

```js
[{
	title: 		 //标题
	bgImg: 		 //背景图片.
	bgImgClick:	 //点击时的背景图片.
}]
```

menuItemConfig：

- 类型：JSON对象
- 默认值：无
- 描述：菜单项配置

内部字段：

```js
{
		titleColor:				//文本颜色,默认“#ffffff”(白色),格式为#fff、#ffffff、rgba(r,g,b,a)等.
		titleSelectColor:		//选中状态时,按钮文本的颜色, 默认“#ffffff”(白色).
		fontSize:				//文字大小,默认11.0.
		textMarginTop:			//文本距离按钮上边界的距离,默认90.0.
}
```

menuConfig：

- 类型：JSON对象
- 默认值：无
- 描述：菜单配置

内部字段：

```js
{
		coverBgColor:	//遮罩背景色,默认“#000000”(黑色)格式为#fff、#ffffff、rgba(r,g,b,a)
		coverAlpha:		//遮罩的透明度, ,默认0.8,取值范围0.0~1.0.
		rows:			//单页每行显示的按钮数,默认4.
}
```

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述: 包含被点击的按钮的相关信息

内部字段：

```js
{
	item:{ 		//对象,表示被点击的按钮.
		type: 	//被点击的按钮所属控件,字符串,可选”bar”, “menu”
		index:	//被点击的按钮的下标. 标签栏和菜单部分的按钮的下标均分别从 0 开始计数
		}
}
```
err:

- 类型: JSON 对象
- 描述: 
- 内部字段:
```js
	{
		msg:			//错误信息.
	}
```

##示例代码

```js
var tabBarMenu = api.require("tabBarMenu");
var theme = "simple"; //可以支持自定义主题,示例内置两种风格题:simple,night.
tabBarMenu.open({ //打开标签菜单.
	defaultBarSelect: 1,//默认选中的标签栏按钮
	autoLayout: true,//是否自动调整当前页面网页视图的位置.
	barConfig: {//标签栏通用配置信息.
				//背景图片路径.
		bgImg: "widget://image/tabBarMenu/" + theme + "/tabbar_bg.png"
    },
	barItemConfig: {//标签栏按钮的通用配置信息.
		//文本颜色, 格式为#fff、#ffffff、rgba(r,g,b,a)等
		titleColor: "#ffffff",
		titleSelectColor: "#ffffff",    			//选中状态时,按钮文本的颜色, 默认与titleColor相同.
		fontSize: 11.0,     						//文字大小.
		textMarginTop: 41.0,   						//文本距离按钮上边界的距离.
		primaryItem: 2      						//激活弹出菜单的标签栏按钮的下标.
	},	
	//标签栏各按钮的信息.
	barItems: [{title: "动态",//标题.
			bgImg: "widget://image/tabBarMenu/" + theme + "/tabbar_icon_auth.png",          				//背景图片路径.
			bgImgClick: "widget://image/tabBarMenu/" + theme + "/tabbar_icon_auth_click.png"      			//被点击时的背景图片路径.
        },
        {title: "与我有关",//标题
			bgImg: "widget://image/tabBarMenu/" + theme + "/tabbar_icon_at.png",//背景图片路径.
			//被点击时的背景图片路径.
			bgImgClick: "widget://image/tabBarMenu/" + theme + "/tabbar_icon_at_click.png"
        },
        {title: "动态", //标题.
			bgImg: "widget://image/tabBarMenu/" + theme + "/tabbar_btn.png",        
			bgImgClick: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_click.png"     
        },
        {title: "玩吧", 
			bgImg: "widget://image/tabBarMenu/" + theme + "/tabbar_icon_more.png", 
			bgImgClick: "widget://image/tabBarMenu/" + theme + "/tabbar_icon_more_click.png" 
        },
        {title: "空间",
			bgImg: "widget://image/tabBarMenu/" + theme + "/tabbar_icon_space.png", 
			bgImgClick: "widget://image/tabBarMenu/" + theme + "/tabbar_icon_space_click.png" 
        }
    ],
    //菜单栏通用配置. 
	menuConfig: {					
		coverBgColor: "#000000", //遮罩的背景色, 格式为#fff、#ffffff、rgba(r,g,b,a)等.  
		coverAlpha: 0.8,//遮罩的透明度, 取值范围0.0~1.0.  
       rows: 4//单页菜单每行显示的按钮数.
    },
    //菜单栏各按钮通用配置信息.
	menuItemConfig: {					
		titleColor: "#ffffff",//文本颜色, 格式为#fff、#ffffff、rgba(r,g,b,a)等.
		titleSelectColor:"#ffffff",//选中状态时,按钮文本的颜色, 默认与titleColor相同.
		fontSize: 11.0,//字体大小.
		textMarginTop: 90.0//文本距离按钮上边界的距离.
    },
    //菜单栏各按钮的信息.
	menuItems: [
		  {title: "说说",//标题.
				bgImg: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_talk.png",//背景图片.  
				//被点击时的背景图片.
				bgImgClick: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_talk_click.png" 
        },
        {title: "照片",      				 
			bgImg: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_transferphotos.png",  
			bgImgClick: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_transferphotos_click.png"  
        },
        {title: "水印相机",
			bgImg: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_watermarkcamera.png",
			bgImgClick: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_watermarkcamera_click.png"
        },
        { title: "视频",
			bgImg: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_video.png", 
			bgImgClick: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_video_click.png" 
        },
        {title: "签到",
			bgImg: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_registration.png", 
			bgImgClick: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_registration_click.png"  

        },
        { title: "连拍",
			bgImg: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_continuousshooting.png", 
		bgImgClick: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_continuousshooting_click.png" 
        },
        {itle: "日志",      				
			bgImg: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_journal.png",
			bgImgClick: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_journal_click.png"  		
        },
        {title: "二维码",
			bgImg: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_2dbarcode.png", 
			bgImgClick: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_2dbarcode_click.png"
        },
        {title: "语音相机",
			bgImg: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_videocamera.png",
			bgImgClick: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_videocamera_click.png"  
        },
        {title: "位置",
			bgImg: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_place.png", 
			bgImgClick: "widget://image/tabBarMenu/" + theme + "/tabbar_btn_popup_place_click.png"  
        }
    ]
}, function(ret, err){ 							//点击标签栏或菜单栏按钮时的回调方法.点击激活菜单栏的标签栏按钮时不会触发此方法.
	if(ret){
		var item = ret.item;
		if("menu " == item.type){
			tabBarMenu.hideMenu();
		}
		api.alert({title: "提示", msg: "您点击了 " + item.type + " 上,第 " + item.index + " 个按钮!", buttons: ["确定"]});
    }
});
```

##补充说明

- 点击菜单栏任意非按钮部分,可以隐藏菜单栏,同时会再次模拟点击员标签栏被选中的按钮一次.
- 每个窗口最多只允许存在一个tabBarMenu.
- 若将 参数 autoLayout设为true, 系统会自动在视图打开,关闭,显示,隐藏时对当前页面网页视图到屏幕底部的距离作出适当调整.

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="2"></div>

关闭

close()

##示例代码

	var tabBarMenu = api.require("tabBarMenu");
	
	tabBarMenu.close();

##补充说明

无

可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setBarSelect**<div id="3"></div>

模拟点击标签栏按钮

setBarSelect({param});

##params

index:

- 类型: 数字
- 默认值: 无
- 说明: 按钮下标

##示例代码

```js
var tabBarMenu = api.require("tabBarMenu");

tabBarMenu.setBarSelect({ 				//设置当前选中的按钮.
    index: 3 							//要设置选中状态的按钮的下标.
});
```

##补充说明

模拟点击,同样会触发按钮的事件响应函数,就像你真的点击了相应的按钮.这对与视图间的联动非常有帮助

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setBadge**<div id="4"></div>

设置徽章

setBadge(params)

##params

item:

- 类型: 对象
- 默认值:：无
- 说明: 要设置徽章的按钮

内部字段:

```js
{ 
	type: 		//按钮所属控件,字符串,可选”bar”, “menu”
	index:		//按钮的下标. 数字,标签栏和菜单部分的按钮的下标均分别从 0 开始计数
}
```

title:

- 类型：字符串
- 默认值: “”
- 说明：要设置的按钮的内容,可为空;为空时,type会自动设为”center”

type:

- 类型：字符串
- 默认值：”center”
- 说明：徽章风格,可选”left”, “center”, “right”,可为空


bgColor:

- 类型：字符串
- 默认值：#ff0000 (红色)
- 说明：徽章的背景色,格式为#fff、#ffffff、rgba(r,g,b,a)等,可为空

titleColor:

- 类型：字符串
- 默认值：#ffffff (白色)
- 说明：文本颜色,格式为#fff、#ffffff、rgba(r,g,b,a)等,可为空

fontSize:

- 类型：数字
- 默认值：11.0
- 说明：字体大小.可为空

marginTop:

- 类型：数字
- 默认值：17.0
- 说明：徽章距离按钮上边缘的距离.可为空

##示例代码

```js
var tabBarMenu = api.require("tabBarMenu");

tabBarMenu.setBadge({ 					//设置徽章.
	item: {
        type: "bar",	    			//按钮所属控件,可选”bar”, “menu”
        index: 0						//按钮的下标. 标签栏和菜单部分的按钮的下标均分别从 0 开始计数
    },
    title: "", 							//要设置的按钮的内容.
    type: "center", 					//徽章风格,可选”left”, “center”, “right”.
	bgColor: "#ff0000",    				//徽章的背景色,格式为#fff、#ffffff、rgba(r,g,b,a)等.
	titleColor: "#ffffff",  			//文本颜色, 格式为#fff、#ffffff、rgba(r,g,b,a)等.
	fontSize: 11.0,   					//字体大小.
	marginTop: 17.0       				//徽章距离按钮上边缘的距离.
});

tabBarMenu.setBadge({ 					//设置徽章.
	item: {
        type: "bar",	    			//按钮所属控件,可选”bar”, “menu”
        index: 3						//按钮的下标. 标签栏和菜单部分的按钮的下标均分别从 0 开始计数
    },
    title: "NEW", 						//要设置的按钮的内容.
    type: "right", 						//徽章风格,可选”left”, “center”, “right”.
	bgColor: "#ff0000",    				//徽章的背景色,格式为#fff、#ffffff、rgba(r,g,b,a)等.
	titleColor: "#ffffff",  			//文本颜色, 格式为#fff、#ffffff、rgba(r,g,b,a)等.
	fontSize: 11.0,   					//字体大小.
	marginTop: 17.0       				//徽章距离按钮上边缘的距离.
});

tabBarMenu.setBadge({ 					//设置徽章.
	item: {
        type: "menu",	    			//按钮所属控件,可选”bar”, “menu”
        index: 3						//按钮的下标. 标签栏和菜单部分的按钮的下标均分别从 0 开始计数
    },
    title: "NEW", 						//要设置的按钮的内容.
    type: "right", 						//徽章风格,可选”left”, “center”, “right”.
	bgColor: "#ff0000",    				//徽章的背景色,格式为#fff、#ffffff、rgba(r,g,b,a)等.
	titleColor: "#ffffff",  			//文本颜色, 格式为#fff、#ffffff、rgba(r,g,b,a)等.
	fontSize: 11.0,   					//字体大小.
	marginTop: 15.0       				//徽章距离按钮上边缘的距离.
});
```

##补充说明

当title为空时,会将type自动设为”center”

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**removeBadge**<div id="5"></div>

移除徽章

removeBadge(params)

##params

type:

- 类型: 字符串
- 默认值: 无
- 说明: 按钮所属控件,可选“bar”, “menu”

index: 

- 类型: 数字
- 默认值: 无
- 说明: 按钮下标.标签栏和菜单部分的按钮的下标均分别从 0 开始计数,互不影响

##示例代码

```js
var tabBarMenu = api.require("tabBarMenu");

tabBarMenu.removeBadge({ 					//移除徽章.
    type: "bar",							//按钮所属控件,可选”bar”, “menu”
    index: 3								//按钮的下标. 标签栏和菜单部分的按钮的下标均分别从 0 开始计数
});

tabBarMenu.removeBadge({ 					//移除徽章.
    type: "menu",							//按钮所属控件,可选”bar”, “menu”
    index: 3								//按钮的下标. 标签栏和菜单部分的按钮的下标均分别从 0 开始计数
});
```

##补充说明

暂无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hide**<div id="6"></div>

隐藏

hide();

##示例代码

	var tabBarMenu = api.require("tabBarMenu");
	
	tabBarMenu.hide();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="7"></div>

显示

show();

##示例代码

	var tabBarMenu = api.require("tabBarMenu");
	
	tabBarMenu.show();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hideMenu**<div id="8"></div>

隐藏弹出菜单

hideMenu();

##示例代码

	var tabBarMenu = api.require("tabBarMenu");
	
	tabBarMenu.hideMenu();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**showMenu**<div id="9"></div>

显示弹出菜单

showMenu();

##示例代码

	var tabBarMenu = api.require("tabBarMenu");
	
	tabBarMenu.showMenu();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
