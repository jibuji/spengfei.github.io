---
layout: post
title:  "利用jekyll搭建自己的博客站点!"
date:   2015-05-07 14:29:34
categories: technology
---

###1. 安装rbenv，该工具可以方便的管理和安装ruby的不同版本###
  参考这个页面中的`Installation`部分.
    `https://github.com/sstephenson/rbenv`
  
###2. 安装ruby-build插件###
  使用如下命令即可：
    `git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build`
    
###3. 安装ruby，下面例子中选择2.2.2的ruby版本:###
  {% highlight bash %}
  rbenv install 2.2.2
  rbenv local 2.2.2
  {% endhighlight bash %}
  
###4. 安装rubyGems，参考如下网址：###
  `https://rubygems.org/pages/download`
  
###5. 安装jekyll，参考如下网址：###
  `http://jekyllrb.com/`
  
