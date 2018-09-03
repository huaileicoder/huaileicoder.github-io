---
layout:     post
title:      "使用jekyll+github pages 搭建个人博客"
subtitle:   " "
date:       2018-09-01
author:     "huailei"
header-img: "img/home-bg-o.jpg"
tags:
    -jekyll -githubpages
    
---

> But I Still Love You

## 搭建原因
作为一个萌新，一直想有一个自己的博客，前一段时间自己试着使用`jekyll+github pages` 来搭建自己的博客，其中有遇到很多的坑，比如搭建jekyll，以及使用jekyll theme的时候，慢慢的自己也搞懂这是个怎么回事，现在也写下这篇文章来记录一下，希望能对有些人有一点点帮助。  

## 搭建环境
搭建博客需要jekyll以及GitHub，其中GitHub提供一个`pages`功能，允许用户自定义项目首页，用来替代默认的源码列表  
- github Pages可以被认为是用户编写的、托管在github上的静态网页  
- Jekyll是一个静态站点生成器，它会根据网页源码生成静态文件   

jekyll官网是这样介绍的
>Jekyll 是一个简单的博客形态的静态站点生产机器。它有一个模版目录，其中包含原始文本格式的文档，通过一个转换器（如 Markdown）和我们的 Liquid 渲染器转化成一个完整的可发布的静态网站，你可以发布在任何你喜爱的服务器上。Jekyll 也可以运行在 GitHub Page 上，也就是说，你可以使用 GitHub 的服务来搭建你的项目页面、博客或者网站，而且是完全免费的

## 开始搭建
### GitHub Pages
首先肯定要使用到GitHub，所以有一个自己的GitHub账号就不要再说了。当有了自己的GitHub账号之后需要创建一个新的仓库，并命名为username.github.io，比如我的username是 
`huaileicoder`，那新建的仓库就是`huaileicoder.github.io`。    
![新建一个仓库](/img/github-create new repository.png)  
创建好之后进入仓库中选择setting，找到`GitHub Pages`，然后将你的site发布到`https://username.github.io/`。  
![github-pages](/img/github-pages.png)
我们去访问`https://username.github.io/`，会发现只有一个简单的页面。   

### 安装jekyll
安装jekyll其实非常简单，但是你得做好一些准备工作，根据jekyll官网上介绍需要：  
- Ruby
- RubyGems  

所以需要前往[https://rubyinstaller.org/downloads/](https://rubyinstaller.org/downloads/)下载`Ruby`以及`DEVELOPMENT KIT `，DEVELOPMENT KIT有不同的版本，可以根据你的系统选择相应的工具。  
安装ruby的时候，根据的你的选择放到相应的盘中，并且勾选`Add Ruby executables to your PATH`。  
安装好ruby之后可以使用指令`ruby -v`查看ruby是否安装完成  
```
C:\Users\Administrator>ruby -v
ruby 2.5.1p57 (2018-03-29 revision 63029) [x64-mingw32]
```
安装dev kit 的时候一般把安装目录改为RubyDevKit，安装好dev-kit之后，使用终端(就是Windows下使用cmd启动的那个小黑窗)进入RubyDevKit目录，然后执行`ruby dk.rb init`，然后使用文本编辑器打开RubyDevKit目录中的`config.yml`。在文件的最后加上`- D:/Ruby25-x64`，这是自己的Ruby安装目录，然后在刚才的终端下执行`ruby dk.rb install`。  
接着在终端中输入`gem -v`，可以看到相应的gem版本。
```
gem -v
2.7.6
```
然后执行`gem install jekyll`安装jekyll，因为jekyll很多安装包是由`bundle`来安装的，并且如果没有的话启动jekyll会报错的，所以需要接着执行`gem install bundle`，也可以直接这样`gem install jekyll bundle`来安装。安装好之后执行`jekyll new dir`，然后在终端中`cd dir`接着执行`bundle install`来安装jekyll的依赖包，可以使用`bundle update`来进行依赖包的更新。所有准备工作都做好之后，那就直接执行`jekyll serve`，会有一些版本不匹配的问题，可以看到终端上会有提示信息让你使用`bundle exec jekyll serve`来启动jekyll，正常启动之后访问`http://127.0.0.1:4000`来进入。这时候我们只能看到一个简单地页面，所以一般我们都会使用到别人已经做好的模板，当然你能力足够的话完全可以自己来写。

## jekyll theme
使用jekyll原始的页面是非常简陋的，所以我们可以使用别人写好的jekyll theme来搭建一个"面相姣好"的博客页面。[这里](http://jekyllthemes.org)有许多模板，你可以挑一款自己喜欢的。我使用的是[Hux](http://huangxuan.me/)修改之后的模板，在[这里](https://github.com/huaileicoder/huxpro.github.io)可以看到你如何修改文件变为你自己的博客，这里只是一个模板，如果你对博客要求的东西不是太多的我想这已经够用了。其中配置`_config.yml`更加详细的信息可以从[jekyll官网](http://jekyllcn.com/)获取。不过需要提醒一句的是文章中涉及到的评论系统`duoshuo`以及`disqus`，`duoshuo`已不能使用，`disqus`很早就被墙了，所以都不能使用，在这里推荐大家使用`gitment`，从网上可以搜到很多的教程来使用`gitment`搭建评论系统。  
另外在对第一次使用模板的时候可以会因为一些配置文件版本问题不匹配，所以需要自己根据实际情况去解决，不过遇到这些文件不匹配的时候可以试着自己使用`bundle install xxxxx`或者`gem install xxxxxx`去安装对应的文件，如果实在安装不了，可以试着从其他地方找到对应版本号的文件粘贴进去，最后实在不行那就安装一个匹配的jekyll，我想这是遇到自己觉得解决不了的问题的时候最简单的方法。

## 后记
当第一次使用`jekyll+github pages`来搭建博客的时候，不知道自己要做什么，就在Google查相关的信息，这样的信息还是不少的，所以在这里感谢那些在网上贡献自己知识的人。我不知道自己多少次安了卸，卸了安，安装的过程中自己根据终端的错误信息，以及网上的教程，就知道什么样的错误该怎么解决，所以呢，如果对这方面不是有些了解的话，你一次就安装成功之后可以卸载，然后自己再按着这样的方式再去安装，安装的时候可以更换ruby的版本，我想你会有不同的体验的。安装的教程也可以参考 [jekyll官网](http://jekyllcn.com/)，里面有更加详细的信息。