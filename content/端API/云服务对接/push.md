/*
Title: push
Description: push
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[bind](#1)

[joinGroup](#2)

[leaveGroup](#3)

[setListener](#4)

[removeListener](#5)

[setPreference](#6)
</div>

#**概述**

push模块提供推送相关操作，包括推送设置、监听推送消息、用户绑定、加入组、退出组等功能

#**bind**<div id="1"></div>

将来自业务系统的用户信息绑定至推送服务器

bind({params}, callback(ret, err))

##params

userName：

- 类型：字符串
- 默认值：无
- 描述：用户名称，来自业务系统，不能为空

userId：

- 类型：字符串
- 默认值：无
- 描述：用户Id，来自业务系统，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:””    //错误描述
}
```

##示例代码

```js
var push = api.require('push');
push.bind({
	userName:'testName',
	userId:'testId'
},function(ret,err){
	if(ret){
		api.alert({msg:ret.status});
	}else{
		api.alert({msg:err.msg});
	}
});
```

##补充说明

绑定用户信息至推送服务器

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**joinGroup**<div id="2"></div>

加入（绑定）某个群组

joinGroup({params}, callback(ret, err))

##params

groupName：

- 类型：字符串
- 默认值：无
- 描述：群组名称，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:””    //错误描述
}
```

##示例代码

```js
var push = api.require('push');
push.joinGroup({
	groupName:'department'
},function(ret,err){
	if(ret){
		api.alert({msg:ret.status});
	}else{
		api.alert({msg:err.msg});
	}
});
```

##补充说明

绑定群组

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**leaveGroup**<div id="3"></div>

退出群组绑定

leaveGroup({params}, callback(ret, err))

##params

groupName：

- 类型：字符串
- 默认值：无
- 描述：群组名称，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:””    //错误描述
}
```

##示例代码

```js
var push = api.require('push');
push.leaveGroup({
	groupName:'department'
},function(ret,err){
	if(ret){
		api.alert({msg:ret.status});
	}else{
		api.alert({msg:err.msg});
	}
});
```

##补充说明

移除群组绑定

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setListener**<div id="4"></div>

注册监听推送消息

setListener(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	data:[]           //消息内容，对象数组
}
```

##示例代码

```js
var push = api.require('push');
push.setListener(
	function(ret,err){
		if(ret){
			api.alert({msg:ret.data});
		}
    }
);
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**removeListener**<div id="5"></div>

移除对推送消息的监听

removeListener()

##示例代码

    var push = api.require('push');
    push.removeListener();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setPreference**<div id="6"></div>

推送偏好设置

setPreference({param})

##params

notify：

- 类型：布尔
- 默认值：true
- 描述：是否弹出消息通知

updateCurrent：

- 类型：布尔
- 默认值：false
- 描述：本次弹出通知是否覆盖更新上一个通知。仅Android平台生效

##示例代码

```js
var push = api.require('push');
push.setPreference({
    notify:true,
    updateCurrent:false
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
