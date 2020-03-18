---
layout: post
author: Vulkey_Chen
title: "HaE - 信息高亮与提取者"
date: 2020-03-18
music-id: 1421271606
permalink: /archives/2020-03-18/1
description: "HaE - 信息高亮与提取者"
---

# HaE - 信息高亮与提取者

## 前言

HaE（Highlight and Extractor），是基于MarkINFO插件（地址：https://github.com/gh0stkey/BurpSuite-Extender-MarkInfo ）的基础进行重构。

用处：
- 高亮标记请求，针对高亮的请求进行深度挖掘
- 敏感信息泄露发现

## 设计想法

语言：Python

![-w902](https://vulkey.oss-cn-hangzhou.aliyuncs.com/2020-03-18/15845160387850.jpg)

功能：
- 自定义正则
- 自定义高亮颜色
- 自定义高亮或提取

## 设计过程

### 可视化界面

UI设计（基于Eclipse可视化设计），基于Java Swing

![-w1143](https://vulkey.oss-cn-hangzhou.aliyuncs.com/2020-03-18/15845162741518.jpg)

然后将Java代码转换为Python代码即可（**有很多坑～**）

使用BurpSuite接口：`ITab`创建Tab

![-w1276](https://vulkey.oss-cn-hangzhou.aliyuncs.com/2020-03-18/15845160114052.jpg)

### 高亮颜色

将BurpSuite的所有高亮颜色集成：（仅支持：`red, orange, yellow, green, cyan, blue, pink, magenta, gray`）

![-w96](https://vulkey.oss-cn-hangzhou.aliyuncs.com/2020-03-18/15844769689459.jpg)

![-w518](https://vulkey.oss-cn-hangzhou.aliyuncs.com/2020-03-18/15845164967615.jpg)

### 配置文件格式

选用JSON格式，格式为

```
name: {"regex": regexText, "highlight": isHighlight, "extract": isExtract, "color": colorText}
```

### 颜色优先级和升级

定义Colors变量：

`colors = ['red', 'orange', 'yellow', 'green', 'cyan', 'blue', 'pink', 'magenta', 'gray']`

利用下标的方式进行优先级排序，当满足2个同颜色条件则以优先级顺序上升颜色。（例如：**两个正则，颜色为橘黄色，该请求两个正则都匹配到了，那么将升级为红色**）

## 使用方法

### 环境设置

进入Extender - Options - Python Environment

![-w840](https://vulkey.oss-cn-hangzhou.aliyuncs.com/2020-03-18/15845168078333.jpg)

载入Jython的Jar包以及载入python的包路径。

加载插件，选择HaE.py文件：

![-w858](https://vulkey.oss-cn-hangzhou.aliyuncs.com/2020-03-18/15845168915243.jpg)

加载成功：

![-w743](https://vulkey.oss-cn-hangzhou.aliyuncs.com/2020-03-18/15845169108559.jpg)


### RUN IT

#### 添加自定义正则

```
名字：Email

正则：[\\w-]+(?:\\.[\\w-]+)*@(?:[\\w](?:[\\w-]*[\\w])?\\.)+[\\w](?:[\\w-]*[\\w])?

高亮颜色：red

是否高亮和提取：是
```

转到HaE标签页，进行设置，点击Add按钮即可添加

![-w1278](https://vulkey.oss-cn-hangzhou.aliyuncs.com/2020-03-18/15845171413470.jpg)

HaE - Config查看是否进行配置，点击Reload按钮：

![-w1277](https://vulkey.oss-cn-hangzhou.aliyuncs.com/2020-03-18/15845172203307.jpg)

#### 高亮请求

在Proxy - HTTP History中可以看见高亮请求，响应标签页中含有`MarkINFO`标签，其中将匹配到的邮箱提取了出来

![-w1268](https://vulkey.oss-cn-hangzhou.aliyuncs.com/2020-03-18/15845175423506.jpg)
