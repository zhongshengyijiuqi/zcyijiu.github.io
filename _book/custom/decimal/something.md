## 引入

``` js
    import Vue from 'vue'
    import {
        Decimal
    } from 'yiyun-app-asby'

    Vue.component(Decimal.name,Decimal)
```
## 代码演示


``` html
    <decimalFormat 
        :positionData="data" 
        @integerFormatBlur="integerFormatBlur"
        @decimalFormatBlur="decimalFormatBlur"
     ></decimalFormat>
```

## 属性
|参数|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|positionData|单行文本小数整数基础数据|Object|-|是|


### integerFormatBlur 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|integerFormatBlur|单行文本整数Blur事件|Object：data，Object：code|

### decimalFormatBlur 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|decimalFormatBlur|单行文本小数Blur事件|Object：data，Object：code|


