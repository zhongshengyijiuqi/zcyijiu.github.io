## 引入

``` js
    import Vue from 'vue'
    import {
        Money
    } from 'yiyun-app-asby'

    Vue.component(Money.name,Money)
```
## 代码演示


``` html
    <moneyFormat 
        :positionData="data" 
        @moneyFormatBlur="moneyFormatBlur" 
    ></moneyFormat>
```

## 属性
|参数|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|positionData|单行文本金额基础数据|Object|-|是|


### moneyFormatBlur 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|moneyFormatBlur|单行文本金额Blur事件|Object：data，Object：code|


