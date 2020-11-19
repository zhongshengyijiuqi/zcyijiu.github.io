## 特殊组件 vant-Picker选择器

## 代码演示


``` html
     <div @click="actionShow = true">选择器</div>
      <van-action-sheet v-model="actionShow" :closeable="false">
         <van-picker show-toolbar title="时间选择" :columns="columns" ref="picker"
          @cancel="pickerCancel"
          @confirm="pickerConfirm"
          @change="pickerChange"
         />
      </van-action-sheet>
```

``` js
export default {
  data(){
    return{
      //选择器
      actionShow:false,
      columns:[
        {
          values:[], //yyyymmdd 星期X 存放器
          defaultIndex:3,
          type:'Year'
        },
        {
          values:(() =>{
            let data = []
            for(let i = 0;i<24;i++){
              let s = i
              data.push(s)
            }
            return data
          })(),
          defaultIndex:2,
          typr:'Branch'
        },
        {
          values:(() =>{
            let data = []
            for(let i = 0;i<60;i++){
              let s = i
              data.push(s)
            }
            return data
          })(),
          defaultIndex:1,
          type:'Second'
        }
      ],
      default_index:0,//当前位置
      totalDateList:[]//yyyymmddhhmmss 格式存放器
    }
  },
  mounted(){
    let currentTiem = new Date()
    let currentYear = currentTiem.getFullYear() //当前年
    let currentTime = currentTiem.getHours() //当前时
    let currentBranch = currentTiem.getMinutes();//当前分
    let currentSecond = currentTiem.getSeconds() //当前秒
    let data = []// 展示数据
    let Adata = []//获取数据
    let obj = this.timeConversion(currentYear)
    data = [...data,...obj.data]
    Adata = [...Adata,...obj.Adata]
    this.columns[0].values = data
    this.columns[0].defaultIndex = this.default_index
    this.columns[1].defaultIndex = currentTime
    this.columns[2].defaultIndex = currentBranch
    this.totalDateList = Adata
  },
  methods:{
    pickerCancel(){ // 取消按钮
      this.actionShow = false
    },
    pickerConfirm(val,index){//确定按钮
      let tiem = this.totalDateList[index[0]] + ' ' +(index[1]<10?'0' + index[1]:index[1]) + ':' + (index[2]<10?'0' + index[2]:index[2])
      this.actionShow = false
    },
    pickerChange(val){//滚动停止后
      let indeses = val.getIndexes()
      let dataTotal = val.getIndexes()[0]
      let maxTotal = this.totalDateList[0] //第一条数据
      let maxYear = new Date(maxTotal).getFullYear()//第一一条数据的 年
      let minTotal = this.totalDateList[this.totalDateList.length -1] //最后一条数据
      let minYear = new Date(minTotal).getFullYear()//最后一条数据的 年
      if(this.totalDateList.length - dataTotal < 30){
        let obj = this.timeConversion(minYear + 1)
        this.columns[0].values = [...this.columns[0].values,...obj.data]
        this.totalDateList = [...this.totalDateList,...obj.Adata]
        this.columns[0].defaultIndex = dataTotal
      }else if(dataTotal < 30){
        let obj = this.timeConversion(maxYear - 1)
        this.columns[0].values = [...obj.data,...this.columns[0].values]
        this.totalDateList = [...obj.Adata,...this.totalDateList]
        this.columns[0].defaultIndex = obj.Adata.length + dataTotal
      }
    },
    timeConversion(Year){ //日期获取
      let data = []
      let Adata = []
      let month = [1,2,3,4,5,6,7,8,9,10,11,12]
      let tiem
      let Atiem
      let currentTiem = new Date()
      let currentYear = currentTiem.getFullYear() //当前年
      let currentDate = currentTiem.getFullYear() + "/" + (parseInt(currentTiem.getMonth()) + 1) + "/" + currentTiem.getDate() //当前年月日
      for(let j = 0;j<month.length;j++){
        let day = this.fanDayByYearMonth(Year,month[j])
        for(let s = 1;s<day+1;s++){
          Atiem = Year + '/' + month[j] + '/' + (s<10?'0' + s:s)
          if(currentDate == Atiem){
            tiem = '今天'
            this.default_index = data.length
          }else{
              if(currentYear != Year){
                tiem =  Year + '/' + month[j] + '/' + (s<10?'0' + s:s) + ' ' + this.weekDay(Atiem)
              }else{
                tiem = month[j] + '/' + (s<10?'0' + s:s) + ' ' + this.weekDay(Atiem)
              }
          }
          data.push(tiem)
          Adata.push(Atiem)
        }
      }
      return {
        Adata:Adata,
        data:data,
      }
    },
    weekDay(date){//xxxx/xx/xx 转周几
      let weekDay = ["星期日", "星期一", "星期二", "星期三", "星期四", "星期五", "星期六"]
      let myDate = (new Date(Date.parse(date))).getDay()
      return weekDay[myDate]
    },
    fanDayByYearMonth(year,month) {//判断当月有几天
      switch (month) {
        case 1:
        case 3:
        case 5:
        case 7:
        case 8:
        case 10:
        case 12:
          return 31;
          break;
        case 2:
          return this.isRunYear(year) ? 29 : 28;
          break;
        case 4:
        case 6:
        case 9:
        case 11:
          return 30;
          break;
      }
    },
    //被四整除（不被100整除）的是闰年，其中可以被100整除的同时必须被400整除的才是闰年，其余的就是平年
    isRunYear(year) {
      return year%4== 0? (year%100 == 0? (year%400==0? true:false) :true) : false;
    },
  }
```

