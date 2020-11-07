## 引入

``` js
    import Vue from 'vue'
    import {
        Personnel
    } from 'yiyun-app-asby'

    Vue.component(Personnel.name,Personnel)
```
## 代码演示


``` html
    <personnelFormat 
        :positionData="data" 
        :personnelRadioDate="personnelTemplateData" 
        @personnelRadioFun="personnelRadioFun" 
    ></personnelFormat>
```

## 属性

|参数|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|positionData|人员基础数据|Object|-|是|
|personnelRadioDate|人员修改数据|Object|-|否|


## 普通控件personnelRadioDate属性

|字段名|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|type|type == positionData.type|number，string|-|是|
|choiceName|choiceName == positionData.choiceName|string|-|是|
|choiceId|choiceId == positionData.choiceId|string|-|是|

## 明细里控件personnelRadioDate属性

|字段名|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|type|type == positionData.type|number，string|-|是|
|choiceName|choiceName == positionData.choiceName|string|-|是|
|choiceId|choiceId == positionData.choiceId|string|-|是|
|fatherId|fatherId == positionData.fatherId |string|-|是|
|sonId|sonId == positionData.sonId |string|-|是|

###### 注：//fatherId为明细ID，//sonid就是唯一资源码，若是不用资源码值可以为自定义值

### personnelRadioFun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|personnelRadioFun|人员点击事件|人员基础数据|

