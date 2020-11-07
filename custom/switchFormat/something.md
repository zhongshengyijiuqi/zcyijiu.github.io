## 引入

``` js
    import Vue from 'vue'
    import {
        SwitchFormat
    } from 'yiyun-app-asby'

    Vue.component(SwitchFormat.name,SwitchFormat)
```
## 代码演示


``` html
    <switchFormat 
        :positionData="data" 
        @switchFun="switchFun"
    ></switchFormat>
```

## 属性
|参数|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|positionData|开关基础数据|Object|-|是|


### switchFun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|switchFun|开关点击事件|开关基础数据|


