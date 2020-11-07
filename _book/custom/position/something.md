## 引入

``` js
    import Vue from 'vue'
    import {
        Position
    } from 'yiyun-app-asby'

    Vue.component(Position.name,Position)
```
## 代码演示


``` html
    <position 
        :positionData="data"  
        :positionR="positionRTemplateData"
        :positionS="positionSTemplateData"
        :positionL="positionLTemplateData"
        :positionG="positionGTemplateData"
        @positionRadioFun="positionRadioFun"
        @positionScanFun="positionScanFun"
        @positionBlur="positionBlur"
        @positionLocFun="positionLocFun"
    ></position>
```

## 属性

|参数|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|positionData|单选,扫码输入,手动填写,自动定位,自动生成基础数据|Object|-|是|
|positionR|单选修改数据|Object|-|否|
|positionS|扫码输入修改数据|Object|-|否|
|positionL|自动定位修改数据|Object|-|否|
|positionG|自动生成修改数据|Object|-|否|


## 普通控件position属性

|字段名|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|type|type == positionData.type|number，string|-|是|
|choiceName|choiceName == positionData.choiceName|string|-|是|
|choiceId|choiceId == positionData.choiceId|string|-|是|

## 明细里控件position属性

|字段名|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|type|type == positionData.type|number，string|-|是|
|choiceName|choiceName == positionData.choiceName|string|-|是|
|choiceId|choiceId == positionData.choiceId|string|-|是|
|fatherId|fatherId == positionData.fatherId |string|-|是|
|sonId|sonId == positionData.sonId |string|-|是|

###### 注：//fatherId为明细ID，//sonid就是唯一资源码，若是不用资源码值可以为自定义值

### positionRadioFun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|positionRadioFun|单选点击事件|单选基础数据|
### positionScanFun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|positionScanFun|扫码输入点击事件|扫码输入基础数据|
### positionBlur 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|positionBlur|手动填写Blur事件|Object：data，Object：code|
### positionLocFun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|positionLocFun|自动定位点击事件|自动定位基础数据|

