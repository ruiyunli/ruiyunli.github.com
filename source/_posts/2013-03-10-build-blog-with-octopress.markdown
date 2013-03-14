---
layout: post
title: "Build Blog With Octopress"
date: 2013-03-10 19:44
comments: true
categories: Octopress
---
`windows环境下基于Octopress的博客搭建和部署`

###搭建 Octopress 本地环境
* 安装 [git for windows](http://help.github.com/win-set-up-git/)

* 安装`ruby`，下载地址: [RubyInstaller](http://rubyforge.org/frs/?group_id=167)，安装版本 [rubyinstaller-1.9.2-p290.exe](http://rubyforge.org/frs/download.php/75127/rubyinstaller-1.9.2-p290.exe)，注意版本是1.9.2
<!-- more -->
* 安装gem编译环境， 下载地址：[DevKit-tdm-32-4.5.2-20111229-1559-sfx.exe](https://github.com/downloads/oneclick/rubyinstaller/DevKit-tdm-32-4.5.2-20111229-1559-sfx.exe)，下载完成后，将其解压到 如 `E:\DevKit`，然后在win的cmd窗口中执行如下命令进行安装：
{% highlight c %}
cd E:\DevKit
ruby dk.rb init
ruby dk.rb instal
{% endhighlight %}

* 安装`python`，下载地址：[activepython](http://www.activestate.com/activepython) ，安装2.7版，主要是博客代码加亮模块需要`python`环境的支持，安装完以后，在win的cmd窗口中执行：
{% highlight c %}
 easy_install pygments 
{% endhighlight %}

###更新配置

* 中文`utf-8`编码的支持，在win xp环境变量中配置如下：
{% highlight c %}
LANG=zh_CN.UTF-8
LC_ALL=zh_CN.UTF-8
{% endhighlight %}

* 变更`gem`的更新源，`ruby`的官方更新源经常被河蟹，木有办法，幸亏国内有淘宝做好事，提供了国内的更新源，这样速度就快多了，变更如下：
{% highlight c %}
gem sources --remove http://rubygems.org/
gem sources -a http://ruby.taobao.org/
gem sources -l
{% endhighlight %}
注意 ：请确保只有 `http://ruby.taobao.org/` 唯一一个条目

* 安装`rdoc`和`bundler`
{% highlight c %}
gem install rdoc bundler
{% endhighlight %}

###安装`Octopress`

* 下载`Octopress`源码
{% highlight c %}
git clone git://github.com/imathis/octopress.git octopress
cd octopress # If you use RVM, You'll be asked if you trust the .rvmrc file (say yes).
ruby --version # Should report Ruby 1.9.2
{% endhighlight %}

* 安装依赖模块
{% highlight c %}
$ vi Gemfile
#将行 ： source "http://rubygems.org/"
#改为 ： source "http://ruby.taobao.org/"
$ bundle install
{% endhighlight %}

* 安装默认主题
{% highlight c %}
rake install
{% endhighlight %}
如若出错：
{% highlight c %}
$ rake install
rake aborted!
You have already activated rake 0.9.2.2, but your Gemfile requires rake 0.9.2. Using bundle exec may solve this.
(See full trace by running task with --trace)
{% endhighlight %}
修正办法为：
{% highlight c %}
$ bundle update; rake install
{% endhighlight %}

###发布博客到`github pages`

* 与`github`建立连接
{% highlight c %}
rake setup_github_pages
{% endhighlight %}
按照提示输入 github page repository的url地址，例如：`git@github.com:RubyLouvre/rubylouvre.github.com.git`

* 生成静态页面
{% highlight c %}
rake generate
{% endhighlight %}

* 本地预览，访问 `http://localhost:4000`,查看博客本地运行效果
{% highlight c %}
rake preview
{% endhighlight %}

* 发送到`github`服务器，访问`http://careychow.github.com`查看博客服务器运行效果
{% highlight c %}
rake deploy
{% endhighlight %}

* 保存博客源码到`github source`分支
{% highlight c %}
git add .
git commit -m 'blog source'
git push origin source
{% endhighlight %}

###配置`Octopress`

* 更新配置文件 `octopress/_config.yml`, ，参考`http://octopress.org/docs/configuring/`，示例如下，若包含中文，请将文件格式保存成utf-8的格式
{% highlight c %}
url: http://share.izzz.org
title: RyanLeo
subtitle: Share With You...
author: RyanLeo
simple_search: http://google.com/search
description:
{% endhighlight %}
* 绑定个人域名
{% highlight c %}
echo 'www.example.com' >> octopress/source/CNAME
{% endhighlight %}
修改域名 `www.example.com` A记录到 `207.97.227.245`,或者`CNAME`到`github-name.github.com`

* 创建新文章和新页面
{% highlight c %}
rake new_post["article name"]
rake new_page["page name"]
{% endhighlight %}
* 发布到`github`个人空间
{% highlight c %}
rake generate
rake deploy
{% endhighlight %}