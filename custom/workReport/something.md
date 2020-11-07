

## 引入

``` js
    import Vue from 'vue'
    import {
        WorkReport
    } from 'yiyun-app-asby'

    Vue.component(WorkReport.name,WorkReport)
```
## 代码演示


``` html
    <workReport :positionData="data" ></workReport>
```

## 属性
|参数|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|positionData|报工单信息基础数据|Object|-|是|
