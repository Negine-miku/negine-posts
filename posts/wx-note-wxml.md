---
title: "wx小程序开发笔记-wxml模板语法"
description: "介绍wxml模板基础语法"
date: "2025-11-24"
tags: ["微信小程序", "wxml"]
---
# 一、基础
### 1.hidden与wx\:if,wx\:elif,wx\:else

```html
<view 
    hidden="true" //是否隐藏---条件显示-display:none/block
    wx:if="true" //是否显示/渲染---条件渲染
    wx:elif="false" //是否显示
    wx:else="false" //是否显示    
    >
    这是一个视图
</view>
```
### 2.wx\:for循环渲染
```html
<view 
    wx:for="{{data}}" 
    wx:key="index" //不需要括号{{}}
    //拓展
    wx:for-item="item" //自定义循环项变量名
    wx:for-index="index" //自定义循环索引变量名
    >
    索引是{{index}}，值是{{item}}
</view>
```