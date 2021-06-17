
## 代码演示


``` html
   <div @click="storageFun">工厂模型单选</div>

        <factory-model-radio
    :show="factoryModelRadioShow" 
    :factoryModelRadioData="factoryModelRadioData"
    @factoryModelRadioFun="factoryModelRadioFun" 
    @factoryModelRadioReturn="factoryModelRadioReturn"
    ></factory-model-radio>
```
``` js
    export default {
        data(){
            return{
            //单选工厂模型
                factoryModelRadioShow:false,
                factoryModelRadioData:{//组织架构
                    deptList:[],
                    departmentList:[],
                    choiceData:[
                    
                    ],
                    multipleChoice:[
                    
                    ],
                },
                factoryModelRadioList:[
                    {
                        "id": "H~00000028",
                        "name": "工位1-1-1-3",
                        "parentId": "44ZPKxtM8bZ",
                        "type": 5,
                        "checked":false,
                        "selection":false
                    },
                    {
                        "id": "H~00000027",
                        "name": "工位1-1-1-2",
                        "parentId": "44ZPKxtM8bZ",
                        "type": 5,
                        "checked":false,
                        "selection":false
                    },
                ],
            }
        },
        mounted(){
            this.getFactoryModelFun()
        },
        methods:{
            //单选 + 工厂模型
            factoryModelRadioFun(item){
                console.log(item)
                this.storageData = item.multipleChoice[0]
                this.factoryModelRadioList = item.multipleChoice
                this.factoryModelRadioShow = false
            },
            factoryModelRadioReturn(){
                this.factoryModelRadioShow = false
            },
            //存储
            storageFun(){
            this.factoryModelRadioData.multipleChoice = this.factoryModelRadioList
            this.factoryModelRadioShow = true
        },
            
        async getFactoryModelFun(){
            try {
                let res = await this.getFactoryModel()
                let masterBranch = []
                let list = []
                let deptConcat = JSON.parse(JSON.stringify(res.data))
                deptConcat.forEach(arr =>{
                    arr.data = []
                    arr.checked = false // 选择 
                    arr.selection = false //是否可选
                    if(arr.type<=3){
                        if(arr.type != 3){
                            arr.selection = true
                        }
                        list.push(arr)
                    }
                })
                list.forEach(arr =>{
                    list.forEach(element =>{ 
                        if(arr.id == element.parentId){
                            arr.data.push(element)
                        }
                    })
                    if(!arr.parentId){ //最顶级人员
                        masterBranch.push(arr)
                    }
                })
                this.factoryModelRadioData.deptList = JSON.parse(JSON.stringify(masterBranch))
                this.factoryModelRadioData.departmentList = JSON.parse(JSON.stringify(res.data))
                console.log('masterBranch',masterBranch)
            } catch (error) {
                console.log('查询所有模型列表',error)
            }
        },
    }
```
<!-- ## 工厂模型（单选） -->


## 属性

|参数|说明|类型|默认值|是否必填|
| ----- | ----- | ----- | ----- | ----- |
|show|控制组件显示隐藏|Boolean|false|是|
|factoryModelRadioData|总数据|Object|{}|是|
|factoryModelRadioData.deptList|第一级数据（树结构）|Array|[]|是|
|factoryModelRadioData.departmentLIst|全部数据|Array|[]|是|
|factoryModelRadioData.multipleChoice|选中数据|Array|[]|是|


### factoryModelRadioFun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|factoryModelRadioFun|选中返回函数|value(选中返回的数据)|

### factoryModelRadioReturn 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|factoryModelRadioReturn|返回键返回函数|-|

