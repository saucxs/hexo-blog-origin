---
layout: post
title: github+hexo搭建自己的博客网站（二）更换主题yilia
date: 2017-08-26 22:01:23
toc: true
tags:
    - 前端
    - hexo
---

开始更换主题，hexo默认的主题是landscape，可以更换为其他的主题yilia主题

如何对如何搭建hexo+github可以查看我第一篇入门文章：http://www.cnblogs.com/chengxs/p/7402174.html

详细的可以查看hexo博客的演示：https://saucxs.github.io/

可以查看在github上生成的静态文件：https://github.com/saucxs/saucxs.github.io.git，如果觉得可以请给颗星星。

 <!--more-->

下面贴出github上star数量最多的前10个主题：

1.iissnan/hexo-theme-next， 3510个star。
2.litten/hexo-theme-yilia， 1703个star。
3.TryGhost/Casper， 679个star。
4.wuchong/jacman， 503个star。
5.A-limon/pacman， 431个star。
6.daleanthony/uno， 416个star。
7.orderedlist/modernist， 367个star。
8.AlxMedia/hueman， 336个star。
9.kathyqian/crisp-ghost-theme， 303个star。
10.xiangming/landscape-plus， 287个star。

 

## 1、clone主题代码

在根目录下执行
``` bash
$ git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia
 ``` 

##2、修改配置文件

修改根目录下的_config.yml文件：
``` bash
theme: yilia    //默认为landscape
 ``` 

## 3、修改themes/yilia/_config.yml文件：

修改为：
``` bash
# Header

menu:
  主页: /
  所有文章: /allPages
  随笔: /tags
  相册: /photos

# SubNav
subnav:
  github: "https://github.com/saucxs"
  weibo: "#"
  rss: /atom.xml
  zhihu: "#"
  #qq: "#"
  #weixin: "#"
  #jianshu: "#"
  #douban: "#"
  #segmentfault: "#"
  #bilibili: "#"
  #acfun: "#"
  #mail: "mailto:litten225@qq.com"
  #facebook: "#"
  #google: "#"
  #twitter: "#"
  #linkedin: "#"



# 是否需要修改 root 路径
# 如果您的网站存放在子目录中，例如 http://yoursite.com/blog，
# 请将您的 url 设为 http://yoursite.com/blog 并把 root 设为 /blog/。
root:

# Content

# 文章太长，截断按钮文字
excerpt_link: 阅读全文
# 文章卡片右下角常驻链接，不需要请设置为false
show_all_link: '展开全文'
# 数学公式
mathjax: false
# 是否在新窗口打开链接
open_in_new: false
fancybox: true
#是否开启动画效果
animate: true

# 打赏
# 打赏type设定：0-关闭打赏； 1-文章对应的md文件里有reward:true属性，才有打赏； 2-所有文章均有打赏
reward_type: 2
# 打赏wording
reward_wording: '谢谢你请我吃糖果'
# 支付宝二维码图片地址，跟你设置头像的方式一样。比如：/assets/img/alipay.jpg
alipay: /assets/img/alipay.jpg
# 微信二维码图片地址
weixin: /assets/img/wechat.png

# 目录
# 目录设定：0-不显示目录； 1-文章对应的md文件里有toc:true属性，才有目录； 2-所有文章均显示目录
toc: 1
# 根据自己的习惯来设置，如果你的目录标题习惯有标号，置为true即可隐藏hexo重复的序号；否则置为false
toc_hide_index: true
# 目录为空时的提示
toc_empty_wording: '目录，不存在的…'

# 是否有快速回到顶部的按钮
top: true

# Miscellaneous
baidu_analytics: ''
google_analytics: ''
favicon: /favicon.png

#你的头像url
avatar:

#是否开启分享
share_jia: true
share_addthis: false

#评论：1、多说；2、网易云跟帖；3、畅言；4、Disqus 不需要使用某项，直接设置值为false，或注释掉
#具体请参考wiki：https://github.com/litten/hexo-theme-yilia/wiki/

#1、多说
duoshuo: false

#2、网易云跟帖
wangyiyun: false

#3、畅言
changyan_appid: false
changyan_conf: false

#4、Disqus 在hexo根目录的config里也有disqus_shortname字段，优先使用yilia的
disqus: false

# 样式定制 - 一般不需要修改，除非有很强的定制欲望…
style:
  # 头像上面的背景颜色
  header: '#4d4d4d'
  # 右滑板块背景
  slider: 'linear-gradient(200deg,#a0cfe4,#e8c37e)'

# slider的设置
slider:
  # 是否默认展开tags板块
  showTags: false

# 智能菜单
# 如不需要，将该对应项置为false
# 比如
#smart_menu:
#  friends: false
smart_menu:
  innerArchive: '所有文章'
  friends: '友链'
  aboutme: '关于我'

friends:
  百度一下: http://www.baidu.com
  友情链接2: http://localhost:4000/
  友情链接3: http://localhost:4000/
  友情链接4: http://localhost:4000/
  友情链接5: http://localhost:4000/
  友情链接6: http://localhost:4000/

aboutme: 小本科一枚<br><br>毕业于沈航，就职于苏宁<br>只是一个前端小开发
 ``` 

## 4、运行
``` bash
hexo clean   //清空之前主题

hexo g     //生成静态文件

hexo s     //在本地运行

hexo d    //发布到github的page上
 ``` 

## 5、写新的博客
``` bash
hexo new '博客文章名字'
 ``` 

## 6、运行测试
``` bash
hexo s -g   //生成静态文件，启动本地服务器
``` 

 

可以查看远程服务器https://github.saucxs.io 



 