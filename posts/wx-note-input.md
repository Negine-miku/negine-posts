---
title: "wx小程序开发笔记-<input/>组件"
description: "介绍<input/>输入组件的使用"
date: "2025-11-24"
tags: ["微信小程序", "input"]
---
:::attention
##### 1.基于 [微信官方文档-小程序-input](https://developers.weixin.qq.com/miniprogram/dev/component/input.html)
##### 2.在js+基础模板中使用。
:::
# 一、基础使用
### 1.创建输入框
```html
<input 
    value="123" //输入框默认值
    type="text" //可不写，默认text
    password="true" //密码输入框
    disabled="true" //是否禁用输入框
    placeholder="请输入" //输入框占位符
    bindinput="handleInput" //输入事件绑定
    />
//type="nickname" 输入昵称
//type="number" 输入数字

```
# 二、基础事件
### 1.bindinput
```js
//输入事件绑定
handleInput(e){
    console.log(e.detail.value);//获取输入框的值
}
```