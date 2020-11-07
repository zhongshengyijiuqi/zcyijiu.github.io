# 介绍

1、Git 是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。

2、Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。

3、Git 与常用的版本控制工具 CVS, Subversion 等不同，它采用了分布式版本库的方式，不必服务器端软件支持。

# 安装
下载Git  官方地址为：https://git-scm.com/download/win

# 常用指令

``` git

git config --global user.name "你的名字或昵称"

git config --global user.email "你的邮箱"

ssh-keygen -t rsa -C "xxxxx@xxxxx.com"

cat ~/.ssh/id_rsa.pub
在c:/Users/“你的用户名”/.ssh路径下，找到id_rsa.pub文件将里面的内容全部复制下来将SSH key添加到码云账户中

git init  //初始化git仓库

git remote rm origin //删除

git remote add origin 你的项目地址 //注:项目地址形式为:http://git.oschina.net/xxx/xxx.git或者 git@git.oschina.net:xxx/xxx.git     用来连接远程码云

git pull origin master  上传前pull下

git add .    //将项目中的所有文件上传

git commit -m '对上传文件的注释'

git push origin master    //正式上传至码云中，若上传有问题，可以试试   git push origin master -f 表示舍弃线上的文件，强制推送

git clone 你的工程url  

git branch //查看本地分

git branch -r //查看远程分支

git branch [name] //创建本地分支：注意新分支创建后不会自动切换为当前分支

git checkout [name] //切换分支

git checkout -b [name] //创建新分支并立即切换到新分支

git branch -d [name] //删除分支：-d选项只能删除已经参与了合并的分支，对于未有合并的分支是无法删除的。如果想强制删除一个分支，可以使用-D选项

git merge [name] //合并：将名称为[name]的分支与当前分支合并

git push origin [name] //创建远程分支(本地分支push到远程)

git push origin :heads/[name] //删除远程分支

npm uninstall xxx //删除插件
```