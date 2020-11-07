# 介绍

##### 移动端组件

# 安装

#### NPM

``` sh
    npm install yiyun-app-ozs
```
如果在一个模块化工程中使用它，必须要通过 `Vue.component()` 明确地安装模块：

``` js
import Vue from 'vue'
import {
    Framework
} from 'yiyun-app-ozs'
import 'yiyun-app-ozs/lib/yiyun-app-assembly.css'

Vue.component(Framework.name,Framework)
```