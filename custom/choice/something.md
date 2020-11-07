## 引入

``` js
    import Vue from 'vue'
    import {
        Choice
    } from 'yiyun-app-asby'

    Vue.component(Choice.name,Choice)
```
## 代码演示


``` html
    <choiceFormat 
        :positionData="data" 
        :choiceCheckboxDate="choiceCheckboxTemplate" 
        @choiceRadioFun="choiceRadioFun" 
        @choiceCheckboxFun="choiceCheckboxFun" 
    ></choiceFormat>
```

## 属性

|参数|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|positionData|单项选择多选选择基础数据|Object|-|是|
|choiceCheckboxDate|单项选择多项选择修改数据|Object|-|否|


## 普通控件choiceCheckboxDate属性

|字段名|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|type|type == positionData.type|number，string|-|是|
|choiceName|choiceName == positionData.choiceName|string|-|是|
|choiceId|choiceId == positionData.choiceId|string|-|是|

## 明细里控件choiceCheckboxDate属性

|字段名|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|type|type == positionData.type|number，string|-|是|
|choiceName|choiceName == positionData.choiceName|string|-|是|
|choiceId|choiceId == positionData.choiceId|string|-|是|
|fatherId|fatherId == positionData.fatherId|string|-|是|
|sonId|sonId == positionData.sonId|string|-|是|

###### 注：//fatherId为明细ID，//sonid就是唯一资源码，若是不用资源码值可以为自定义值

### choiceRadioFun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|choiceRadioFun|单项选择点击事件|单项选择基础数据|
### choiceCheckboxFun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|choiceCheckboxFun|多项选择点击事件|多项选择基础数据|

