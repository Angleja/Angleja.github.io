---
layout:       post
title:        "HXPro使用心得！"
author:       "Angle"
header-style: text
catalog:      true
tags:
    - Blog
    - Other
---

> 先说背景，本人非计算机相关专业，未接触过前端开发，自学过部分html和css。以此，写这篇博客来学习本博客搭建框架。

# 编译环境搭建
# 1. 安装Ruby和Bundle
Ruby是一种纯粹的面向对象编程语言。Ruby 是一种为前端和后端Web 开发以及其他类似应用程序而设计的脚本语言。 它是一种强大的，动态类型的，面向对象的语言，具有高级语法，使编程感觉就像英语编码。安装链接[点Here](www.ruby-lang.org/en/)。
安装后可查看版本。

```sh
$ ruby -v
```
Bundler 能够跟踪并安装所需的特定版本的 gem，以此来为 Ruby 项目提供一致的运行环境。
Bundler 是 Ruby 依赖管理的一根救命稻草，它可以保证你所要依赖的 gem 如你所愿地出现 在开发、测试和生产环境中。 利用 Bundler 启动项目简单到只用一条命令：`bundle install`。

```sh
$ gem install bundler
```
稍微解释一下gem。RubyGems 是 Ruby 的一个包管理器，它提供一个分发 Ruby 程序和库的标准格式，还提供一个管理程序包安装的工具。

RubyGems 旨在方便地管理 gem 安装的工具，以及用于分发 gem 的服务器。这类似于 Ubuntu 下的apt-get, Centos 的 yum，Python 的 pip。
```
gem install #
gem uninstall  #
gem list --local  #列出本地可用的包
$ gem sources -l  #查看当前源
```
# 2. 安装依赖包
在项目目录下，Bundle会根据目录下一个叫Gemfile文件里声明的依赖安装相关包。
```sh
$ bundle install 
```
以本项目的Gemfile为例.
```
source 'https://rubygems.org'
gem 'jekyll-paginate'

gem "jekyll", "~> 4.0"
gem "rake"

gem "webrick", "~> 1.7"
```
首先，他告诉 bundler 默认是在Gemfile里指定的https://rubygems.org上来找 gem。接着，你声明了一些依赖：

* 任意版本的jekyll-paginate
* 版本是>= 4.0，但是<5.0的jekyll
* 类似的webrick
  
如果任何需要的 gem 已经被安装了，bundler 会直接使用它们。在你的系统上安装完所有的 gem 后，bundler 会写一个所有这些 gem 和它们的版本号的快照到 Gemfile.lock 里。
# 3. 编译运行
只需要下面一条命令即可编译。
```
$ bundle exec jekyll serve
```
`bundle execute XXX`在一个gem包的上下文中执行一个命令。

Jekyll 是一个简单的博客形态的静态站点生产机器。它有一个模版目录，其中包含原始文本格式的文档，通过一个转换器（如 Markdown）和我们的 Liquid 渲染器转化成一个完整的可发布的静态网站，你可以发布在任何你喜爱的服务器上。

`$ jekyll serve`一个开发服务器将会运行在本地，方便预览。还有一些可以配置的配置选项. 很多配置选项既可以在命令行中作为标识(flags)设定，也可以在源文件根目录中的 _config.yml 文件中进行设定。Jekyll 会自动加载这些配置。

参考链接[Here](http://jekyllcn.com/docs/structure/)