/*
Title: trans
Description: trans
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[parse](#1)

[saveImage](#2)

[decodeImgToBase64](#3)
</div>

#**概述**

trans是一个数据格式转换工具，可以实现不同格式数据间的转换，如json，xml

#**parse**<div id="1"></div>

将xml文件或数据解析成JSON对象

parse({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 默认值：无
- 描述：xml文件路径，可为空

data：

- 类型：字符串
- 默认值：无
- 描述：xml数据，可为空

customKey：

- 类型：字符串
- 默认值：plainText
- 描述：所解析的xml值无对应的key时，需要填充一个自定义key，可为空

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：xml解析成的JSON数据

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:            //错误信息
}
```

##示例代码

```js
var trans = api.require('trans');
trans.parse({
	path:'fs://1.xml'
},function(ret,err){
	if(ret) {
		api.alert({msg:'解析成功'});
    }else{
		api.alert({msg:err.msg});
	}
});
```

##补充说明

path和data不能同时为空，如果都不为空，则使用data的值；

如果xml数据中出现类似以下内容：

```js
<author email=''123@api.com''>
	api
</author>
则author节点被解析成以下格式，其中plainText为约定好的字段
{
	email:'123@api.com',
	plainText:'api'
}
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本




#**saveImage**<div id="2"></div>

将base64字符串保存为图片

parse({params}, callback(ret, err))

##params

base64Str：

类型：字符串
默认值：无
描述：要转换成为图片的字符串，不可为空

album：

类型：布尔值
默认值：false
描述：转换后的图片是否保存到系统相册，可为空

imgPath：

类型：字符串
默认值：apicloud.png
描述：转换后的图片保存路径，可为空，为空不保存

imgName：

类型：字符串
默认值：apicloud.png
描述：转换后的图片保存名字，若imgPath下已存在同名图片则覆盖，若imgPath为空则此参数无意义，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```JS
{
	status：		//是否保存成功
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:		//错误信息
}
```

##示例代码

```js
var trans = api.require('trans');
trans.saveImage({
	base64Str:'testStr'
},function(ret,err){
	if(ret.status) {
		api.alert({msg:'解析成功'});
    }else{
		api.alert({msg:err.msg});
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**decodeImgToBase64**<div id="3"></div>

将图片转换为base64字符串

parse({params}, callback(ret, err))

##params

imgPath：

- 类型：字符串
- 默认值：无
- 描述：要转换的图片路径，不可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status：			//是否保存成功
	base64Str:    	//转换后的base64字符串
} 
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:            //错误信息
}
```

##示例代码

```js
var trans = api.require('trans');
trans.decodeImgToBase64({
	imgPath:'fs://1.png'
},function(ret,err){
	if(ret.status) {
		api.alert({msg:ret.base64Str});
    }else{
		api.alert({msg:err.msg});
    }
});
```

##补充说明

支持png、jpg格式的图片

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

