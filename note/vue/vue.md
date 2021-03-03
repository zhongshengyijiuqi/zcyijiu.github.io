# 介绍 vue2.x和vue3.x

本人工作中记录下来的笔记和一些本人感觉花里胡哨的东西。持续记录中。
### 2.x

##### 什么是生命周期函数，在某一时刻会自动执行的函数


![Image text](https://images2018.cnblogs.com/blog/1341218/201807/1341218-20180726161418133-1878075753.png)


``` js
    beforeCreate(){
        //在实例生成之前会自动执行函数
    }
    created(){
        //在实例生成之后会自动执行函数
    }
    beforeMount(){
        //在模板渲染完成前执行的函数
    }
    mounter(){
        //在模板渲染完成后执行的函数
    }
    beforeUpdate(){
        //在data()里面的值改变之前执行的函数
    }
    Update(){
        //在data()里面的值改变之后执行的函数
    }
    beforeUnmount(){
        // vue应用失效时，会自动执行的函数
    }
    unmounted(){
        //vue应用失效时，且DOM完全销毁之后，会自动执行的函数
    }
```

##### v-once   一次渲染不渲染第二次

##### 模板动态参数

``` js
    data(){
        return{
            name:'title1',
            message:'js',
            event:'click'
        }
    },
    template:`
        <h2 :[name]="js" @[event]="ent"></h2>
    `
```

##### 模板修饰符 prevent (阻止默认事件) stop （防止事件冒泡） capture （与事件冒泡的方向相反，事件捕获由外到内） self （只会触发自己范围内的事件，不包含子元素）


##### 计算属性的特性

``` js 

conputed:{ // 当计算属性的依赖的内容发生改变时才会重新计算

},
methods:{//只要页面重新渲染，就会重新执行方法

},

```

### 按键和鼠标修饰符 

``` js
    // @keyup.xxxx
    // .delete    delete（删除）/BackSpace（退格）
    // .tab    Tab
    // .enter    Enter（回车）
    // .esc    Esc（退出）
    // .space    Space（空格键）
    // .left    Left（左箭头）
    // .up    Up（上箭头）
    // .right    Right（右箭头）
    // .down    Down（下箭头）
    // .ctrl    Ctrl
    // .alt    Alt
    // .shift    Shift
    // .meta    (window系统下是window键，mac下是command键)

    // 组合写法    按键组合
    // @keyup.alt.67=”function”    Alt + C
    // @click.ctrl=”function”    Ctrl + Click
    // @keyup.ctrl.c=”function”    Ctrl + C
    // @keyup.ctrl.c+@keyup.c=”function”    Ctrl + C

    // @click 鼠标按钮修饰符
    // .left　　点击鼠标左键即可触发事件
    // .right　　点击鼠标右键即可触发事件
    // .middle　　按下滑轮触发事件
```

### v-model 修饰符
``` js
    // .lazy 懒加载修饰符
    // .number 修饰符让其转换为 number 类型
    // .trim 修饰符可以自动过滤掉输入框的首尾空格。
```


### 3.x


##### 生命周期函数
``` js
    steUp(){
        //在实例生成之前,可代替beforeCreate，created
    }
    onBeforeMount(() =>{
        console.log('组件挂载到页面之前onBeforeMount')
    })
    onMounted(() =>{
      console.log('组件挂载页面之后onMounted')
    })
    onBeforeUpdate(() =>{
      console.log('组件更新之前onBeforeUpdate')
    })
    onUpdated(() =>{
      console.log('组件更新之后onBeforeUpdate')
    })
    onBeforeUnmount(() =>{
        console.log('组件卸载之前onBeforeUnmount')
    })
    onUnmounted(() =>{
        console.log('组件卸载之后onBeforeUnmount')
    })
    onActivated(() =>{
        console.log('在<keep-alive></keep-alive>里面才有')
    })
    onDeactivated(() =>{
        console.log('比如从 A 组件，切换到 B 组件，A 组件消失时执行。')
    })
    onErrorCaptured(() =>{
        console.log('当捕获一个来自子孙组件的异常时激活钩子函数')
    })
    onRenderTracked(() =>{
        console.log('状态跟踪，它会跟踪页面上所有响应式变量和方法的状态，也就是我们用return返回去的值，他都会跟踪。只要页面有update的情况，他就会跟踪，然后生成一个event对象，我们通过event对象来查找程序的问题所在。')
    })
    onRenderTriggered(() =>{
        console.log('它不会跟踪每一个值，而是给你变化值的信息，并且新值和旧值都会给你明确的展示出来。')
    })
```

##### Teleport方法

``` html
    <template>
        <teleport to="#modal">
            <div id="center">
            <h2>JSPang11</h2>
            </div>
        </teleport>
    </template>
    //然后我们在打开/public/index.html,增加一个model节点。
    <div id="app"></div>
    <div id="modal"></div>
    //这时候在浏览器中预览，就会发现，现在组件已经挂载到model节点上了，这就是teleport组件的使用了。
```


##### Suspense异步请求组件

``` html
    <template>
        <div>
            <Suspense>
                <template #default>
                    <h1>删除001</h1>
                </template>
                <template #fallback>
                    <h1>Loading...</h1>
                </template>
            </Suspense>
        </div>
    </template>
    <!--可以看到Suspense是有两个template插槽的，第一个default代表异步请求完成后，显示的模板内容。fallback代表在加载中时，显示的模板内容。-->
```