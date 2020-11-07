## 引入

``` js
    import Vue from 'vue'
    import {
        Time
    } from 'yiyun-app-asby'

    Vue.component(Time.name,Time)
```
## 代码演示


``` html
    <timeFormat 
        :positionData="data" 
        :timeDate="timeTemplateData" 
        @timeFun="timeFun" 
    >
    </timeFormat>
```

## 属性
|参数|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|positionData|日期选择基础数据|Object|-|是|
|timeDate|日期选择修改数据|Object|-|否|

## 普通控件timeDate属性

|字段名|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|type|type == positionData.type|number，string|-|是|
|choiceName|choiceName == positionData.choiceName|string|-|是|
|choiceId|choiceId == positionData.choiceId|string|-|是|

## 明细里控件timeDate属性

|字段名|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|type|type == positionData.type|number，string|-|是|
|choiceName|choiceName == positionData.choiceName|string|-|是|
|choiceId|choiceId == positionData.choiceId|string|-|是|
|fatherId|fatherId == positionData.fatherId |string|-|是|
|sonId|sonId == positionData.sonId |string|-|是|




### timeFun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|timeFun|日期选择点击触发函数|日期选择基础数据|

