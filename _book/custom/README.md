# 介绍

##### 移动端自定义表单控件（开发请结合PC端自定义表单）

# 安装

#### NPM

``` sh
    npm install yiyun-app-asby
```
如果在一个模块化工程中使用它，必须要通过 `Vue.component()` 明确地安装模块：

``` js
import Vue from 'vue'
import {
    Position
} from 'yiyun-app-asby'
import 'yiyun-app-asby/lib/yiyun-app-assembly.css'

Vue.component(Position.name,Position)
```
