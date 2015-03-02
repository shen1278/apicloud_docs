/*
Title: cityList
Description: cityList
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[hide](#3)

[show](#4)
</div>

#**概述**

cityList是一个城市列表模块，自带了右边字母导航条，可快速滚动到目标城市选项。开发者可自定义城市列表的数据源

![图片说明](/img/docImage/cityList.jpg)

#**open**<div id="1"></div>

打开城市列表

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 默认值：0
- 描述：城市列表视图左上角点坐标，可为空

y：

- 类型：数字
- 默认值：100
- 描述：城市列表视图左上角点坐标，可为空

<del>width：</del>

- <del>类型：数字</del>
- <del>默认值：无</del>
- <del>描述：视图的宽，可为空</del>

<del>height：</del>

- <del>类型：数字</del>
- <del>默认值：无</del>
- <del>描述：视图的高，可为空</del>

w：

- 类型：数字
- 默认值：当前屏幕的宽
- 描述：视图的宽，可为空

h：

- 类型：数字
- 默认值：w+20
- 描述：视图的高，可为空

currentCity：

- 类型：字符串
- 默认值：无
- 描述：用户当前所在城市，不可为空

resource：

- 类型：字符串
- 默认值：无
- 描述：城市列表的数据源文件路径，不可为空

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：将此模块视图添加到指定窗口的名字，可为空

##callback(ret, err)

ret：

类型：JSON对象

内部字段：

```js
{
    cityInfo:{}   //返回用户选择的城市信息
}
```

##示例代码

```js
var obj = api.require('cityList');
obj.open({
	currentCity:'北京',
	resource:'widget://res/cityList.json'
},function(ret,err) {
	var cityInfo = ret.cityInfo;
});
```

##补充说明

打开城市列表

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="2"></div>

关闭城市列表

close()

##示例代码

    var obj = api.require('cityList');
    obj.close();

##补充说明

关闭城市列表

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="3"></div>

隐藏城市列表

hide()

##示例代码

    var obj = api.require('cityList');
    obj.hide();

##补充说明

隐藏城市列表

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="4"></div>

显示已隐藏的城市列表

show()

##示例代码

    var obj = api.require('cityList');
    obj.show();

##补充说明

显示已隐藏的城市列表

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
