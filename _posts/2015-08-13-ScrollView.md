---
title: 'React Native Components ScrollView'
date: 2015-08-03 22:32:00
description: React Native文档中文翻译
---

## ScrollView
包裹了 ```ScrollView``` 的组件，同时提供了一体的触控锁定响应系统。

记住 ```ScrollView``` 必须有一个固定的高度才能工作，因为它们包含了一个不定高度的子元素在一个固定容器（通过滚动交互）。为了固定 ```ScrollView``` 的高度，要么直接设置页面高度，或者确保父页面高度是固定的。不要通过 ```{flex: 1}``` 降低页面，这样将导致错误，元素选择器一般在这里用于调试。

目前不支持其他包含的响应阻止滚动页面变成一个响应。

### 属性
