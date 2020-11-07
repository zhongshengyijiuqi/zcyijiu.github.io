## 引入

``` js
    import Vue from 'vue'
    import {
        Upload
    } from 'yiyun-app-ozs'

    Vue.component(Upload.name,Upload)
```
## 代码演示


``` html
    <upload :list="imgList" @change="imgChange" :distinguish="true" :limist="10" :complex="false" accepts="image" num="3"/>
```
<!-- ## 组织架构（单选）Framework.vue -->


## 属性

|参数|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|imgList|已上传的文件列表|FileListItem[]|-|是|
|accept|允许上传的文件类型|string|image|否|
|distinguish|区分标识  每一个上传事件只存一张图 true为存多张，false为存单张|Boolean|false|否|
|limist|图片大小限制 最大10|Number|2|否|
|complex|选中标识，true为单选false多选|Boolean|true|否|
|num|图片限制条数|Number|3|否|

## accept 可选值
|参数|说明|类型|
| ----- | ----- | ----- |
|image|图片|image/*|
|application|表单文件|doc.docx.ppt.pptx.xlsx.xls.pdf|
|video|视频文件|MP4|
|attApplication|通用|doc.docx.ppt.pptx.xlsx.xls.pdf,图片|

``` js
export default {
  data(){
    return{
      //上传文件
      imgList:[]
    }
  },
  mounted(){

  },
  methods:{
    //上传文件
    imgChange(imgList) {
      this.imgList = imgList;
    },
  }
```

### imgChange 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|imgChange|图片上传|value(选中返回的数据)|

