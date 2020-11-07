## 引入

``` js
    import Vue from 'vue'
    import {
        OptionsPageRadio
    } from 'yiyun-app-ozs'

    Vue.component(OptionsPageRadio.name,OptionsPageRadio)
```
## 代码演示


``` html
    <div @click="individual">单项选择</div>
    <optionsPageRadio 
        :optionsPageShow="individualShow" 
        :options="individualData"
        :optionsPageData="individualPageData"

        @optionsDataFun="singleChoice" 
        @optionsReturnFun="choiceRun"
        @searchDataFun="choiceSearch"
        @pullingUpEnd="choicePullingUpEnd"
        @pullingDownEnd="choicepullingDownEnd"
      >
      </optionsPageRadio>
```
<!-- ## 组织架构（单选）Framework.vue -->


## 属性

|参数|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|optionsPageShow|控制组件显示隐藏|Boolean|false|是|
|options|总数据|Object|{}|是|
|optionsPageData|选中数据|Object|{}|是|

``` js
export default {
  data(){
    return{
      //单项选择
      individualShow:false,
      individualData:[{
        id:1,
        name:'测试001',
        checked:false
      },{
        id:2,
        name:'测试002',
        checked:false
      },{
        id:3,
        name:'测试003',
        checked:false
      }],
      individualPageData:{
        title:"列表",
        judge:true,//是否第一次
        isTotal:true,//是否有数据
        page:1,//页数
        data:[]
      },
      optionsCode:null
    }
  },
  mounted(){

  },
  methods:{
    //单项选择
    individual(){
      this.individualShow = true
    },
    singleChoice(item){//单项选择
      this.individualPageData.data = item
      this.individualShow = false
    },
    choiceRun(){//返回
      this.individualShow = false
    },
    choiceSearch(item){//搜索
      this.optionsCode = item.optionsCode
    },
    choicePullingUpEnd(){//下拉加载
      console.log('下拉加载')
    },
    choicepullingDownEnd(){//上拉刷新
      console.log('上拉刷新')
    },
  }
```

### optionsDataFun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|optionsDataFun|选中返回函数|value(选中返回的数据)|
### optionsReturnFun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|optionsReturnFun|返回键返回函数|-|
### searchDataFun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|searchDataFun|搜索事件|obj.optionsCode|

### pullingUpEnd 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|searchDataFun|下拉加载|-|

### pullingDownEnd 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|searchDataFun|上拉刷新|-|

