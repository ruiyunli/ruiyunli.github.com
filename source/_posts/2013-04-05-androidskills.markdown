---
layout: post
title: "AndroidSkills"
date: 2013-04-05 15:59
comments: true
categories: 
---

###About Menu

* showAsAction可以修改为ifroom或者always，是否显示

* 在手机中，竖屏状态下text是不会显示的，切换到横屏才会显示text

* 图标可以到Android网站下载`http://developer.android.com/design/downloads/index.html`

<!-- more -->
###About PreferenceActivity

* xml文件保存在res/xml文件夹下面

* 对onChangePerferenceListener和OnClickPerferenceListener两个函数，返回TRUE分别表示更新值和已经处理响应，返回FALSE分别表示不保存newValue和没有处理响应

* 取得值，getString(key,"unset")

* 设置值，edit().putstring(key,"newValue");

###Eclipse Line Number

* Ctrl+ F10