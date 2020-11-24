## 引入

``` js
    import Vue from 'vue'
    import {
        LoadingPage
    } from 'yiyun-app-ozs'

    Vue.component(LoadingPage.name,LoadingPage)
```
## 代码演示


``` html
      <loading-page  
      :loading="false" 
      background="rgba(255,255,255,0.6)" 
      text="加载中.." 
      textColor="#f00"
       textSize="20" 
       loatype="spinner" 
       customColor="#f00" 
       customSize="40"> 
        <template>
         //插槽
        </template>
       </loading-page>
```
<!-- ## 组织架构（单选）Framework.vue -->


## 属性

|参数|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|loading|控制组件显示隐藏|Boolean|false|是|
|background|遮罩层背景颜色|String|rgba(0,0,0,0.5)|否|
|text|显示在加载图标下方的加载文案|Staring|-|否|
|textColor|加载文案颜色|String|#666666|否|
|textSize|加载文案字体大小|String-Number|14|否|
|customColor|Loading 颜色|String|#409eff|否|
|customSize|Loading 大小|String-Number|20|否|
|loatype|loading类型，可选spinner，wave|String|circular|否|
