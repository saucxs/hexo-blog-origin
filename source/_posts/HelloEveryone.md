---
layout: post
title: HelloEveryone
date: 2017-08-21 09:17:10
tags:
---

##前言
 github提供的page，hexo提供的静态博客文档，
如何对如何搭建hexo+github可以查看我第一篇入门文章：http://www.cnblogs.com/chengxs/p/7402174.html
详细的可以查看hexo博客的演示：https://saucxs.github.io/
hexo+github博客网站源码(可以clone，运行，看到博客演示。觉得可以给颗星星)：https://github.com/saucxs/hexo-blog-origin.git
hexo+github上生成的静态文件：https://github.com/saucxs/saucxs.github.io.git
 <!--more-->
使用github pages服务搭建博客的好处有：
全是静态文件，访问速度快；
免费方便，不用花一分钱就可以搭建一个自由的个人博客，不需要服务器不需要后台；
可以随意绑定自己的域名，不仔细看的话根本看不出来你的网站是基于github的；
数据绝对安全，基于github的版本管理，想恢复到哪个历史版本都行；
博客内容可以轻松打包、转移、发布到其它平台；

##一、github相关设置

###1、在github上创建一个项目

注意：项目名称必须为自己   github的用户名.github.io


 ###2、代码库的设置

开启gh-pages功能，点击界面右侧的Settings，你将会打开这个库的setting页面，向下拖动，直到看见GitHub Pages。

之前是需要：点击Automatic page generator，Github将会自动替你创建出一个gh-pages的页面。 如果你的配置没有问题，那么大约15分钟之后，yourname.github.io这个网址就可以正常访问了~ 如果yourname.github.io已经可以正常访问了，那么Github一侧的配置已经全部结束了。

现在不需要设置page generator。就可以访问https://saucxs.github.io/


##二、安装hexo

###1、全局安装hexo-cli指令
``` bash
npm install hexo-cli -g
``` 
查看hexo版本
``` bash
hexo -v
``` 

###2、初始化hexo
``` bash
hexo init
``` 
hexo会自动下载一些文件到这个目录，包括node_modules，目录结构如下图：

 

###3、开始体验hexo

hexo g
生成静态文件到public文件夹，没有public文件夹就会自动创建，如果有了就会覆盖public内容。

public文件夹的内容是要提交到github上的。



###4、开启本地服务

hexo s
hexo s是开启本地预览服务，打开浏览器访问 http://localhost:4000 即可看到内容，很多人会碰到浏览器一直在转圈但是就是加载不出来的问题，一般情况下是因为端口占用的缘故，因为4000这个端口太常见了，解决端口冲突问题。



 

 ##三、如何将hexo与github page联系起来

 分为3步：

1、配置SSH key

2、设置Git的user name和email

3、配置deployment

 

###1、配置SSH key

如果你之前已经配置好git个人信息，请跳过这一个 步骤，直接来到

为什么要配置这个呢？因为你提交代码肯定要拥有你的github权限才可以，但是直接使用用户名和密码太不安全了，所以我们使用ssh key来解决本地和服务器的连接问题。

$ cd ~/. ssh #检查本机已存在的ssh密钥
如果提示：No such file or directory 说明你是第一次使用git。
``` bash
ssh-keygen -t rsa -C "邮箱"
``` 
然后连续3次回车，最终会生成一个文件在用户目录下，



 打开用户目录，找到.ssh\id_rsa.pub文件，记事本打开并复制里面的内容，打开你的github主页，进入个人设置 -> SSH and GPG keys -> New SSH key：

刚复制的内容粘贴到key那里，title随便填，保存。 



 

测试一下是否成功
``` bash
$ ssh -T git@github.com # 注意邮箱地址不用改
``` 

看到这个信息说明SSH已配置成功！

 

###2、设置Git的user name和email
``` bash
$ git config --global user.name "liuxianan"// 你的github用户名，非昵称
$ git config --global user.email  "xxx@163.com"// 填写你的github注册邮箱
``` 
设置这个是为了便与之后上传到github的page上。

 

###3、设置deployment

配置_config.yml中有关deploy的部分：

正确写法：
``` bash
deploy:
  type: git
  repository: git@github.com:saucxs/saucxs.github.io.git
  branch: master
  ``` 
错误写法：
``` bash
deploy:
  type: github
  repository: https://github.com/saucxs/saucxs.github.io.git
  branch: master
  ``` 
后面一种写法是hexo2.x的写法，现在已经不行了，无论是哪种写法，此时直接执行hexo d的话一般会报如下错误：
``` bash
Deployer not found: github 或者 Deployer not found: git
```

需要安装一个插件
``` bash
npm install hexo-deployer-git --save
```
再次输入hexo d，就ok了。

 

 

自己的github的page，显示如下



 

同时，你的github上的项目，代码已经更新。



 

##四、保留CNAME、README.md等文件

提交之后网页上一看，发现以前其它代码都没了，此时不要慌，一些非md文件可以把他们放到source文件夹下，这里的所有文件都会原样复制（除了md文件）到public目录。

由于hexo默认会把所有md文件都转换成html，包括README.md，所有需要每次生成之后、上传之前，手动将README.md复制到public目录，并删除README.html。

 

##五、修改hexo的主题

在 Hexo 中有两份主要的配置文件，其名称都是 _config.yml。 其中，一份位于站点根目录下，主要包含 Hexo 本身的配置；另一份位于主题目录下，这份配置由主题作者提供，主要用于配置主题相关的选项。

为了描述方便，在以下说明中，将前者称为 站点配置文件， 后者称为 主题配置文件。

PS：需要特别注意的地方是，冒号后面必须有一个空格，否则可能会出问题。

举个栗子：

###1. 安装 NexT

载主题

如果你熟悉 Git， 建议你使用 克隆最新版本 的方式，之后的更新可以通过 git pull 来快速更新， 而不用再次下载压缩包替换。

在终端窗口下，定位到 Hexo 站点目录下。使用 Git checkout 代码：
``` bash
git clone https://github.com/iissnan/hexo-theme-next themes/next
``` 
###2. 启用主题

与所有 Hexo 主题启用的模式一样。 当 克隆/下载 完成后，打开 站点配置文件， 找到 theme 字段，并将其值更改为 next。

启用 NexT 主题

theme: next
到此，NexT 主题安装完成。下一步我们将验证主题是否正确启用。在切换主题之后、验证之前， 我们最好使用 hexo clean 来清除 Hexo 的缓存。
``` bash
hexo clean
``` 
``` bash
hexo s -g      //生成静态文件，启动本地服务
 ``` 

##六、 写博客

定位到我们的hexo根目录，执行命令：
``` bash
hexo new ‘HelloEveryone’
``` 

我们只需要打开这个文件就可以开始写博客了，默认生成如下内容

 

 当然你也可以直接自己新建md文件，用这个命令的好处是帮我们自动生成了时间。

 

默认情况下，生成的博文目录会显示全部的文章内容，如何设置文章摘要的长度呢？

答案是在合适的位置加上<!--more-->即可，例如：



##七、访问我的hexo+github博客

可以访问我的git博客来查看效果： https://saucxs.github.io/ 