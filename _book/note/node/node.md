# 介绍

1、NodeJS是为了开发高性能的服务器而诞生的一种技术

2、是运行在服务端的 JavaScript，基于V8（谷歌浏览器的版本）进行运行 

3、使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效

# 前端学习NodeJs的意义

1、 开发沟通：开发时更容易理解后端实现，降低交流成本

2、 后端开发：想写些自己感兴趣的项目时，可以自己独立完成，即使没有后端支持，且成本特别低。

3、 中间层开发：为了进一步的前后端分离，提高性能，使用nodejs做中间层是一个非常好的实践（由于nodejs具有异步io的特点）

# 安装

下载NodeJs  官方地址为：http://nodejs.cn/download/

# 常用模块
``` node
    Geddy
```
Geddy 是一个用于 NodeJS 的 web 开发框架，遵循 MVC，其目标是易用、模块化和高性能。

``` node
    node-dev
```
node-dev 模块是一个开发工具，当你的 js 文件修改保存后，他会自动重启服务进程。

``` node
    node_redis
```
是为 NodeJS 而写的 Redis client，它支持所有 Redis 命令。

``` node
    html2jade
```
html2jade 模块可以方便的转换现有的 HTML 到 Jade 格式。目前仅支持 OS X 和 Linux 平台。

``` node
    xml2js
```
xml2js 基于 sax-js模块，提供简单的 xml 到 Javascript 对象的转换，如需解析 DOM ，jsdom更合适。

``` node
    mailer
```
NodeJS 邮件发送模块，支持定制基于 Mustache 的模板正文。
``` node
    Nide
```
Nide是一个基于Web的开源的Node.js IDE，在MIT License下开源，代码托管于GitHub。其设计思想是简单、易用。
``` node
    jsdom
```
W3C DOM 的 Javascript 实现。
``` node
    Dox
```
兼容 Markdown, JSDoc 格式的文档生成器
``` node
    Jade
```
Jade 模板引擎，是 express 默认的模板引擎。
``` node
    socket.io
```
适合构建跨浏览器的实时应用，提供类似 WebSockets 的API。
``` node
    uglify-js
```
Javascript 解析和压缩、格式化工具。
``` node
    mongoosejs
```
Mongoose 是 MongoDB 数据库的模型工具，为 NodeJS 设计，工作于异步环境下。

# npm常用指令

``` npm
1、npm install <name> --save

2、npm view moduleNames //查看node模块的package.json文件夹

注意事项：如果想要查看package.json文件夹下某个标签的内容，可以使用$npm view moduleName labelName

3、npm list //查看当前目录下已安装的node包

注意事项：Node模块搜索是从代码执行的当前目录开始的，搜索结果取决于当前使用的目录中的node_modules下的内容。

4、npm list parseable=true //可以目录的形式来展现当前安装的所有node包

5、npm help //查看帮助命令

6、npm view moudleName dependencies //查看包的依赖关系

7、npm view moduleName repository.url //查看包的源文件地址

8、npm view moduleName engines //查看包所依赖的Node的版本

9、npm help folders //查看npm使用的所有文件夹

10、npm rebuild moduleName //用于更改包内容后进行重建

11、npm outdated //检查包是否已经过时，此命令会列出所有已经过时的包，可以及时进行包的更新

12、npm update moduleName //更新node模块

13、npm uninstall moudleName //卸载node模块

14、npm help json //一个npm包是包含了package.json的文件夹，package.json描述了这个文件夹的结构。访问npm的json文件夹的方法如下

注意事项：此命令会以默认的方式打开一个网页，如果更改了默认打开程序则可能不会以网页的形式打开。

15、npm search packageName //发布一个npm包的时候，需要检验某个包名是否已存在

16、npm init //会引导你创建一个package.json文件，包括名称、版本、作者这些信息等

17、npm root //查看当前包的安装路径

18、npm root -g //查看全局的包的安装路径

19、npm -v //查看npm安装的版本
```