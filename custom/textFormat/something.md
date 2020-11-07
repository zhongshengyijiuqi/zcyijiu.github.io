## 引入

``` js
    import Vue from 'vue'
    import {
        TextFormat
    } from 'yiyun-app-asby'

    Vue.component(TextFormat.name,TextFormat)
```
## 代码演示


``` html
    <textFormat 
        :positionData="data" 
        @textFormatBlur="textFormatBlur" 
        @textareaFormatBlur="textareaFormatBlur" 
    ></textFormat>
```

## 属性
|参数|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|positionData|文本格式基础数据|Object|-|是|


### textFormatBlur 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|textFormatBlur|若格式为单行文本，为单行文本Blur事件|Object：data，Object：code|

### textareaFormatBlur 事件
|事件名|说明|回调参数|
| ----- | ----- | ----- |
|textareaFormatBlur|若格式为多行文本，为多行文本Blur事件|Object：data，Object：code|
