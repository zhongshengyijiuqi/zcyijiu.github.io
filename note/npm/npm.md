# 介绍

1、npm 是 JavaScript 世界的包管理工具，并且是 Node.js 平台的默认包管理工具。通过 npm 可以安装、共享、分发代码,管理项目依赖关系。

# 安装

下载NodeJs  官方地址为：http://nodejs.cn/download/  并安装npm依赖包

# 使用NPM管理公共模块库 常用指令

``` npm
npm init //命令初始化当前项目信息

```

首先需要在 package.json 添加组件信息

name: 包名，该名不能和已有的名称冲突；

version: 版本号，不能和历史版本号相同；

description: 简介；

main: 入口文件，应指向编译后的包文件；

keyword：关键字，以空格分割；

author：作者；

private：是否私有，需要修改为 false 才能发布到 npm；

license：开源协议。

```
npm login //登入npm 没有账号的要注册账号并绑定邮箱

npm publish //发布到npm上面
```