/*
Title: baiduLocation
Description: baiduLocation
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">


<div class="outline">
[startLocation](#a1)

[stopLocation](#a2)

[getLocation](#a3)
</div>

#**概述**

baiduLocation封装了百度定位的相关功能，使用此模块可获取当前位置信息

#**startLocation**<div id="a1"></div>

开始定位

startLocation({params},callback(ret, err))
##params
accuracy：

- 类型：字符串
- 默认值：100m
- 描述：精度（详见[精度](!Constant)常量），不能为空

filter：

- 类型：数字
- 默认值：1.0
- 描述：位置更新所需最小距离（单位米）

autoStop：

- 类型：布尔
- 默认值：true
- 描述：获取到位置信息后是否自动停止定位

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    status:true                //操作成功状态值
    longitude:116.213          //经度
    latitude:39.213            //纬度
    timestamp:1396068155591    //时间戳
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    msg:""    //错误描述
}
```

##示例代码

```js
var baiduLocation = api.require('baiduLocation');
baiduLocation.startLocation({
    accuracy: '100m',
    filter:1,
    autoStop: true
}, function(ret, err){
    var sta = ret.status;
    var lat = ret.latitude;
    var lon = ret.longitude;
    var t = ret.timestamp;
    if(sta){
        var str = '经度：'+ lon +'<br>';
        str += '纬度：'+ lat +'<br>';
        str += '更新时间：'+ t +'<br>';
    } else{
        api.alert({msg:err.msg});
    }
});
```

##补充说明

开始定位

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**stopLocation**<div id="a2"></div>

停止定位

stopLocation()

##示例代码

```js
var baiduLocation = api.require('baiduLocation');
baiduLocation.stopLocation();
```

##补充说明

停止定位

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getLocation**<div id="a3"></div>

获取位置信息

getLocation(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    longitude:116.213           //经度
    latitude:39.213             //纬度
    timestamp:1396068155591     //时间戳
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    msg:""    //错误描述
}
```

##示例代码

```js
var baiduLocation = api.require('baiduLocation');
baiduLocation.getLocation(
    function(ret, err){
        var sta = ret.status;
        var lat = ret.latitude;
        var lon = ret.longitude;
        var t = ret.timestamp;
        if(sta){
            var str = '经度：'+ lon +'<br>';
            str += '纬度：'+ lat +'<br>';
            str += '更新时间：'+ t +'<br>';
            api.alert({msg:str});
        } else{
            api.alert({msg:err.msg});
        }
    }
);
```

##补充说明

获取位置信息

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
</div>

<div id="const-content">
<div class="outline">
[精度](#a100)
</div>

#**精度**<div id="a100"></div>

定位精度，定位时只返回精度范围内的坐标。字符串类型

##取值范围：

- 10m
- 100m
- 1km
- 3km
</div>