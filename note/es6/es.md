# 介绍

《ECMAScript 6 入门教程》是一本开源的 JavaScript 语言教程，全面介绍 ECMAScript 6 新引入的语法特性。

ES6 与上一个版本 ES5 的所有不同之处，对涉及的语法知识给予详细介绍，并给出大量简洁易懂的示例代码。

本人工作中记录下来的笔记。持续记录中。

``` js
    let a = 10
    var b = 11
    const c = 12
```
##### vue里面用 let { foo, bar } = { foo: 'aaa', bar: 'bbb' };

``` js
    let {foo} = this.$data 
```

##### es6 中的简单去重 new Set（Array）

``` js
    //直接使用 new Set（Array）拿到的不是数组是一个set对象

    Array.from(new Set（Array）)
```
##### 获取两个数组中不同的元素

``` js
    var arr1 = [1,2,3,4,5,6,7,8]
    var arr2 = [1,2,3]
    var delArr = []
    delArr = arr1.concat(arr2).filter(function(v, i, arr) {
        return arr.indexOf(v) === arr.lastIndexOf(v);
    });
```

##### for 、foreach、map 的区别

``` js
var array = [1, 2, 3, 4];
for (var k = 0, length = array.length; k < length; k++) {
 console.log(array[k]);
 break //语句用于跳出代码块或循环
 continue//语句用于立即终止本轮循环，返回循环结构的头部，开始下一轮循环。
 return// 退出代码块或循环并返回
}

[].forEach(function(value, index, array) {
  // forEach方法中的function回调支持3个参数，第1个是遍历的数组内容；第2个是对应的数组索引，第3个是数组本身。
  // forEach方法 是不能直接用break ,continue,return 会报错 只能结合 try catch 使用 强制抛出错误 然后停止循环
      
    }
});
try{
  var array = ["first","second","third","fourth"];
  // 执行到第3次,结束循环
  array.forEach(function(item,index) {
    if(item == "third"){
      throw new Error("EndIterative");
    }
    console.log(item); // first second
  });
}catch(e){
  if(e.message != "EndIterative") throw e;
}
// 下面的代码不影响继续执行
console.log("继续执行。。。");


var data=[1,3,4]
var Squares=data.map(function(val,index,arr){
  console.log(arr[index]==val);  // ==> true
  return val*val           
})
console.log(Squares);        // ==> [1, 9, 16] 生成新数组
```

##### 清空字符串前后空格 trim()，trimStart()消除字符串头部的空格，trimEnd()消除尾部的空格

``` js
const s = '  abc  ';

s.trim() // "abc"
s.trimStart() // "abc  "
s.trimEnd() // "  abc"
```

##### Number.isFinite()和Number.isNaN()

``` js
Number.isFinite()//用来检查一个数值是否为有限的 即不是Infinity。
Number.isFinite(15); // true
Number.isFinite(0.8); // true
Number.isFinite(NaN); // false
Number.isFinite(Infinity); // false
Number.isFinite(-Infinity); // false
Number.isFinite('foo'); // false
Number.isFinite('15'); // false
Number.isFinite(true); // false

Number.isNaN()//用来检查一个值是否为NaN。
Number.isNaN(NaN) // true
Number.isNaN(15) // false
Number.isNaN('15') // false
Number.isNaN(true) // false
Number.isNaN(9/NaN) // true
Number.isNaN('true' / 0) // true
Number.isNaN('true' / 'true') // true
```

##### 合并数组
``` js
var a = [1,2,3]
var b = [4,5,6]
var c = [7,8,9]
[...a,...b,...c]  //[1,2,3,4,5,6,7,8,9]
```

##### 数组实例的find方法，用于找出第一个符合条件的数组成员。

``` js
[1, 4, -5, 10].find((n) => n < 0)
// -5
```

##### Object.keys返回一个数组，包括对象自身的（不含继承的）所有可枚举属性（不含 Symbol 属性）的键名。
``` js
var l = {'add':[{name:"123"},,{name:"345"}]}
Object.keys(l) // ["add"]
```
##### Object.values方法返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键值。
``` js
const obj = { foo: 'bar', baz: 42 };
Object.values(obj)
// ["bar", 42]
```
##### Object.assign()方法用于对象的合并，将源对象（source）的所有可枚举属性，复制到目标对象（target）。
``` js
const target = { a: 1 };

const source1 = { b: 2 };
const source2 = { c: 3 };

Object.assign(target, source1, source2);
target // {a:1, b:2, c:3}
//注意，如果目标对象与源对象有同名属性，或多个源对象有同名属性，则后面的属性会覆盖前面的属性。
```


##### JS函数生成器，function* () {}

``` js
function* fn() {
        console.log(1);
        //暂停！
        yield;
        //调用next方法继续执行
        console.log(2);
    }
    var iter = fn();
    iter.next(); //1
    iter.next(); //2
    //1、函数生成器特点是函数名前面有一个‘*’
　　//2、通过调用函数生成一个控制器
　　//3、调用next()方法开始执行函数
　　//4、遇到yield函数将暂停
　　//5、再次调用next()继续执行函数
```