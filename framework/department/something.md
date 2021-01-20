
## 代码演示


``` html
   <div @click="taskLeaderBoxduo">组织架构多选加部门</div>

          <frameworkDepartment
      :optionsShow="optionsBoxduoShow" 
      :frameworkDepartment="frameworkBoxduoData"
      @frameworkDepartmentCheckboxFun="frameworkCheckboxduoFun" 
      @frameworkDepartmentReturnFun="frameworkreturnBoxduoFun"
      ></frameworkDepartment>
```
``` js
    export default {
        data(){
            return{
            //人员+部门多选
                optionsBoxduoShow:false,
                frameworkBoxduoData:{//组织架构
                    deptList:[],
                    departmentList:[],
                    choiceData:[ //人员选中集合
                    
                    ],
                    multipleChoice:[//部门选中集合
                    
                    ],
                },
                multipleSonduo:[
                    {
                        active: true,
                        checked: false,//选择  人员有选择状态  部门没有
                        data: [],//部门下级
                        deptIdList: [],
                        fatherName: "后端",//所属上级部门名称
                        id: "3u2i7Y8xVCj",
                        isWhether: true,//是否为人员
                        name: "zqp",
                        profilePicture: "https://dl-platform.effio.cn/84217038-aa79-4bb8-a499-5dd0fc7ef06b/user-head/137384615141574997944474.gif",
                        selection: false,//选中 部门有选中状态 人员选中状态
                    }
                ],
                multipleChoice:[
                    {
                        checked: false,  //选择  人员有选择状态  部门没有
                        data: [],//部门下级
                        id: "1211841814905937920",
                        isWhether: false,//是否为人员
                        name: "前端",
                        parentId: "",
                        selection: false,//选中 部门有选中状态 人员选中状态
                    }
                ],
            }
        },
        mounted(){
            this.getDeptListFun()
        },
        methods:{
            taskLeaderBoxduo(){
                this.optionsBoxduoShow = true
                this.frameworkBoxduoData.choiceData = this.multipleSonduo
                this.frameworkBoxduoData.multipleChoice = this.multipleChoiceList
            },
            //多选 + 部门
            frameworkCheckboxduoFun(item){
                console.log(item)
                this.multipleSonduo = item.multipleSon
                this.multipleChoiceRadioList = item.multipleChoice
                this.optionsBoxduoShow = false
            },
            frameworkreturnBoxduoFun(){
                this.optionsBoxduoShow = false
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
                    this.frameworkBoxduoData.deptList = JSON.parse(JSON.stringify(deptConcatlist)) 
                    this.frameworkBoxduoData.departmentList = JSON.parse(JSON.stringify(this.deptConcat))
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
|frameworkDepartment|总数据|Object|{}|是|
|frameworkDepartment.deptList|第一级数据（树结构）|Array|[]|是|
|frameworkDepartment.departmentLIst|部门+人员全部数据|Array|[]|是|
|frameworkDepartment.choiceData|人员选中数据|Array|[]|是|
|frameworkDepartment.multipleChoice|部门选中数据|Array|[]|是|


### frameworkDepartmentCheckboxFun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|frameworkCheckboxFun|选中返回函数|value(选中返回的数据)|
### frameworkDepartmentReturnFun 事件

|事件名|说明|回调参数|
| ----- | ----- | ----- |
|frameworkreturnBoxFun|返回键返回函数|-|

