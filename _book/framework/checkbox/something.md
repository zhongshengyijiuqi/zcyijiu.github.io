## 引入

``` js
    import Vue from 'vue'
    import {
        FrameworkCheckbox
    } from 'yiyun-app-ozs'

    Vue.component(FrameworkCheckbox.name,FrameworkCheckbox)
```
## 代码演示


``` html
    <div @click="taskLeaderBox">组织架构多选</div>

    <frameworkCheckbox 
      :optionsShow="architectureRadio" 
      :frameworkData="architectureData" 
       @frameworkCheckboxFun="frameworkCheckboxFun" 
       @frameworkreturnBoxFun="frameworkreturnBoxFun"
    ></frameworkCheckbox>
```
``` js
    export default {
        data(){
            return{
            //多选
                frameworkBoxData:{//组织架构多选
                    deptList:[],
                    departmentList:[],
                    choiceData:[],
                },
                optionsBoxShow:false,
                multipleSon:[]
            }
        },
        mounted(){
            this.getDeptListFun()
        },
        methods:{
            taskLeaderBox(){
                this.optionsBoxShow = true
                this.frameworkBoxData.choiceData = this.multipleSon
            },
            //多选
            frameworkCheckboxFun(item){
                this.multipleSon = item
                this.optionsBoxShow = false
            },
            frameworkreturnBoxFun(){
                this.optionsBoxShow = false
            },
            
           async getDeptListFun(){//获取组织部门
                try {
                    let res = await this.getDeptList()
                    let deptList = []
                    res.forEach(arr => {
                        deptList.push(arr.id)
                        arr.data = []
                        arr.isWhether = false //是否为人员
                        arr.selection = false //选中 部门有选中状态 没有选中状态
                        arr.checked = false // 选择  人员有选择状态  部门没有
                    });
                    deptList.push('-1')
                    this.deptList = res
                    this.deptConcat = JSON.parse(JSON.stringify(res))
                    this.postMemberInfoByDeptFun()
                } catch (error) {
                    console.log('获取组织部门',error)
                }
            },
           async postMemberInfoByDeptFun(){
                try {
                    let departmentList = await this.postMemberInfoByDept({page:1,num:1000,isAll:true,deptIdList:deptList})
                    departmentList.forEach(arr =>{
                        arr.data = []
                        arr.isWhether = true
                        arr.selection = false
                        arr.checked = false
                    })
                    let departmentData = JSON.parse(JSON.stringify(departmentList))
                    departmentData.forEach(arr =>{
                        this.deptConcat.push(arr)
                    })
                    this.departmentList = this.deptConcat
                    let personalList = []
                    departmentList.forEach(arr =>{
                    departmentList.forEach(element =>{ // 查询数据 分辨父子
                        element.deptIdList.forEach(list =>{
                        if(arr.id == list){
                            element.fatherName = arr.name
                            arr.data.push(element)
                        }
                        })
                    })
                    if(arr.deptIdList.length == 0){ //最顶级人员
                        personalList.push(arr)
                        }
                    })
                    this.deptList.forEach(arr =>{
                        departmentList.forEach(element =>{ // 部门 下的子集归纳
                            element.deptIdList.forEach(list =>{
                            if(arr.id == list){
                                element.fatherName = arr.name
                                arr.data.push(element)
                            }
                            })
                        })
                    })
                
                    this.deptList.forEach(arr =>{ // 部门数据分辨父子
                        this.deptList.forEach(element =>{
                            if(arr.id == element.parentId){
                            element.fatherName = arr.name
                            arr.data.push(element)
                            }
                        })
                    })
                    let deptConcatlist = []
                
                    this.deptList.forEach(arr =>{ //最顶级 部门处理
                    if(!arr.parentId){
                        deptConcatlist.push(arr)
                    }
                    })
                    deptConcatlist.push(...personalList); //最顶级部门 人员合并
                    this.frameworkBoxData.deptList = JSON.parse(JSON.stringify(deptConcatlist)) 
                    this.frameworkBoxData.departmentList = JSON.parse(JSON.stringify(this.deptConcat))
                } catch (error) {
                    console.log('按部门查成员',error)
                }
            },
        },
    }
```
<!-- ## 组织架构（单选）Framework.vue -->


## 属性

|参数|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|optionsShow|控制组件显示隐藏|Boolean|false|是|
|frameworkData|总数据|Object|{}|是|
|frameworkData.deptList|第一级数据（树结构）|Array|[]|是|
|frameworkData.departmentLIst|部门+人员全部数据|Array|[]|是|
|frameworkData.choiceData|选中数据|Array|[]|是|


### frameworkCheckboxFun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|frameworkCheckboxFun|选中返回函数|value(选中返回的数据)|
### frameworkreturnBoxFun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|frameworkreturnBoxFun|返回键返回函数|-|

