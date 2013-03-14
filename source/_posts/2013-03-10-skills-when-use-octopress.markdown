---
layout: post
title: "Skills When Use Octopress"
date: 2013-03-10 19:48
comments: true
categories: Ocropress
---
`以下均为Windows系统中使用总结`

###关于UTF8编码

* 先使用`rake new_post["FileName"]`
* 使用`Notepad++`打开文件，并编辑
* 格式->转为UTF-8无BOM编码格式，保存
* `rake generate & rake preview`

<!-- more -->

###添加标签分类

* `One category`

{% highlight c %}
categories: Sass
{% endhighlight %}

* `Multiple categories example 1`

{% highlight c %}
categories: [CSS3, Sass, Media Queries]
{% endhighlight %}

* `Multiple categories example 2`

{% highlight c %}
categories:
	- CSS3
	- Sass
	- Media Queries
{% endhighlight %}

###添加Disqus

* 编辑`_config.yml`，修改下面的内容

{% highlight c %}
# Disqus Comments
disqus_short_name: shareizzzorg
disqus_show_comment_count: true
{% endhighlight %}

###关于加速网站

* 在`_config.yml`中关掉`twitter`

###关于`Read More...`

* 在某一篇博文的文字间如果使用`<!-- more -->`，则后面的文字都将不会显示，而出现一个`Read On->`的按钮

###关于`404`

* 在`source`目录下添加`404.html`页面

`http://www.360doc.com/content/12/0216/17/1016783_187135339.shtml`

* 在`octopress\source\_includes\custom中的navigation.html`中添加

`<li><a href="{{ root_url }}/../about">About</a></li>`

* `rake generate`

###关于`NavigationBar`

*在`octopress\source\_includes\custom`中的`navigation.html`中添加标签

* 在所添加的标签所指向的文件夹中添加`makedown`文件或者`html`文件

###关于代码高亮

* 在代码区的两端加上标签，区前加`{% highlight c %}`，区后加`{% endhighlight %}`，其中C为语言种类