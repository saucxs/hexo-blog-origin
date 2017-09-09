---
layout: post
title: github+hexo搭建自己的博客网站（三）主题之外的一些基本配置(图片位置，文章目录功能)
date: 2017-09-08 14:44:34
comments: true
categories: 工作
toc: true
tags:
    - 前端
    - hexo
---

使用的yilia主题之后，还需要进行自己的定制配置(图片位置，文章目录功能)

<!--more-->

## 1、图片的位置

比如打赏的支付宝二维码图片，是在当前博客的source/assets/img/下 （不是当前主题）

配置：(在yilia主题下文件里themes\yilia文件夹下的_config.yml)

``` bash

# 打赏基础设定：0-关闭打赏； 1-文章对应的md文件里有reward:true属性，才有打赏； 2-所有文章均有打赏
reward_type: 1
# 打赏wording
reward_wording: '谢谢你请我吃糖果'
# 支付宝二维码图片地址，跟你设置头像的方式一样。比如：/assets/img/alipay.jpg
alipay: /assets/img/alipay.jpg
# 微信二维码图片地址
weixin: /assets/img/weixin.png

``` 

![](/assets/other/pic02.png)


## 2、添加文章目录功能

### 2.1添加css样式

打开themes\yilia\source下的main.266c1c.css文件，添加如下代码

``` bash

/* 新添加的 */
#container .show-toc-btn,#container .toc-article{display:block}
.toc-article{z-index:100;background:#fff;border:1px solid #ccc;max-width:250px;min-width:150px;max-height:500px;overflow-y:auto;-webkit-box-shadow:5px 5px 2px #ccc;box-shadow:5px 5px 2px #ccc;font-size:12px;padding:10px;position:fixed;right:35px;top:129px}.toc-article .toc-close{font-weight:700;font-size:20px;cursor:pointer;float:right;color:#ccc}.toc-article .toc-close:hover{color:#000}.toc-article .toc{font-size:12px;padding:0;line-height:20px}.toc-article .toc .toc-number{color:#333}.toc-article .toc .toc-text:hover{text-decoration:underline;color:#2a6496}.toc-article li{list-style-type:none}.toc-article .toc-level-1{margin:4px 0}.toc-article .toc-child{}@-moz-keyframes cd-bounce-1{0%{opacity:0;-o-transform:scale(1);-webkit-transform:scale(1);-moz-transform:scale(1);-ms-transform:scale(1);transform:scale(1)}60%{opacity:1;-o-transform:scale(1.01);-webkit-transform:scale(1.01);-moz-transform:scale(1.01);-ms-transform:scale(1.01);transform:scale(1.01)}100%{-o-transform:scale(1);-webkit-transform:scale(1);-moz-transform:scale(1);-ms-transform:scale(1);transform:scale(1)}}@-webkit-keyframes cd-bounce-1{0%{opacity:0;-o-transform:scale(1);-webkit-transform:scale(1);-moz-transform:scale(1);-ms-transform:scale(1);transform:scale(1)}60%{opacity:1;-o-transform:scale(1.01);-webkit-transform:scale(1.01);-moz-transform:scale(1.01);-ms-transform:scale(1.01);transform:scale(1.01)}100%{-o-transform:scale(1);-webkit-transform:scale(1);-moz-transform:scale(1);-ms-transform:scale(1);transform:scale(1)}}@-o-keyframes cd-bounce-1{0%{opacity:0;-o-transform:scale(1);-webkit-transform:scale(1);-moz-transform:scale(1);-ms-transform:scale(1);transform:scale(1)}60%{opacity:1;-o-transform:scale(1.01);-webkit-transform:scale(1.01);-moz-transform:scale(1.01);-ms-transform:scale(1.01);transform:scale(1.01)}100%{-o-transform:scale(1);-webkit-transform:scale(1);-moz-transform:scale(1);-ms-transform:scale(1);transform:scale(1)}}@keyframes cd-bounce-1{0%{opacity:0;-o-transform:scale(1);-webkit-transform:scale(1);-moz-transform:scale(1);-ms-transform:scale(1);transform:scale(1)}60%{opacity:1;-o-transform:scale(1.01);-webkit-transform:scale(1.01);-moz-transform:scale(1.01);-ms-transform:scale(1.01);transform:scale(1.01)}100%{-o-transform:scale(1);-webkit-transform:scale(1);-moz-transform:scale(1);-ms-transform:scale(1);transform:scale(1)}}.show-toc-btn{display:none;z-index:10;width:30px;min-height:14px;overflow:hidden;padding:4px 6px 8px 5px;border:1px solid #ddd;border-right:none;position:fixed;right:40px;text-align:center;background-color:#f9f9f9}.show-toc-btn .btn-bg{margin-top:2px;display:block;width:16px;height:14px;background:url(http://7xtawy.com1.z0.glb.clouddn.com/show.png) no-repeat;-webkit-background-size:100%;-moz-background-size:100%;background-size:100%}.show-toc-btn .btn-text{color:#999;font-size:12px}.show-toc-btn:hover{cursor:pointer}.show-toc-btn:hover .btn-bg{background-position:0 -16px}.show-toc-btn:hover .btn-text{font-size:12px;color:#ea8010}

.toc-article li ol, .toc-article li ul {
    margin-left: 30px;
}
.toc-article ol, .toc-article ul {
    margin: 10px 0;
}

``` 

这个代码在也放到了github上：https://github.com/saucxs/saucxs.github.io下的main.266c1c.css文件

### 2.2修改article.ejs文件

使用的是Hexo的toc函数
打开themes\yilia\layout\_partial文件夹下的article.ejs文件
然后若想要文章显示目录，在每篇文章开头加入：toc: true

``` bash
   <!-- 目录内容 -->
        <% if (!index && post.toc){ %>
            <p class="show-toc-btn" id="show-toc-btn" onclick="showToc();" style="display:none">
            <span class="btn-bg"></span>
            <span class="btn-text">文章导航</span>
            </p>
            <div id="toc-article" class="toc-article">
                <span id="toc-close" class="toc-close" title="隐藏导航" onclick="showBtn();">×</span>
                <strong class="toc-title">文章目录</strong>
                <%- toc(post.content) %>
           </div>
           <script type="text/javascript">
            function showToc(){
                var toc_article = document.getElementById("toc-article");
                var show_toc_btn = document.getElementById("show-toc-btn");
                toc_article.setAttribute("style","display:block");
                show_toc_btn.setAttribute("style","display:none");
                };
            function showBtn(){
                var toc_article = document.getElementById("toc-article");
                var show_toc_btn = document.getElementById("show-toc-btn");
                toc_article.setAttribute("style","display:none");
                show_toc_btn.setAttribute("style","display:block");
                };
           </script>
        <% } %>     
   <!-- 目录内容结束 -->
        
```


``` bash
layout: post
title: HelloEveryone-braveToWorld
date: 2017-08-22 09:17:10
toc: true
tags:
    - 杂谈
    - 笔记
```
![](/assets/other/pic01.png)

 