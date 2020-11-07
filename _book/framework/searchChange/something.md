## 引入

``` js
    import Vue from 'vue'
    import {
        SearchChange
    } from 'yiyun-app-ozs'

    Vue.component(SearchChange.name,SearchChange)
```
## 代码演示


``` html
    <div @click="pageSearch">页面搜索</div>
    <searchChange 
      :searchHidden="searchHidden" 
      searchTitle="标题" 
      :searchTime="2000" 
      :historyData="historyData"
      :eject="true"
      
      @returnFun="searchRun"
      @delWhole="delWhole"
      @searchHistory="searchHistory"
      @searchDataFun="searchChange"
      ></searchChange>
```
<!-- ## 组织架构（单选）Framework.vue -->


## 属性

|参数|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|searchHidden|控制组件显示隐藏|Boolean|false|是|
|eject|是否进来弹出键盘|Boolean|false|否|
|searchTitle|页面标题|Staring|搜索|否|
|searchTime|搜索间隔|Number|1000|否|
|historyData|历史记录|Array|[]|否|



``` js
export default {
  data(){
    return{
      //页面搜索
      searchHidden:false,
      historyData:[]//历史记录
    }
  },
  mounted(){

  },
  methods:{
    //页面搜索
    pageSearch(){
      this.searchHidden = true
    },
    searchRun(){//返回
      this.searchHidden = false
    },
    delWhole(){//删除全部历史记录

    },
    searchHistory(item){//点击历史记录搜索
      console.log(item)
    },
    searchChange(item){//搜索
      console.log(item.searchCode)
    },
  }
```

### searchRun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|searchRun|返回|-|

### delWhole 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|delWhole|历史记录全部删除|-|


### searchHistory 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|searchHistory|历史记录点击搜索|value(选中返回的数据)|

### searchDataFun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|searchDataFun|搜索|value|

