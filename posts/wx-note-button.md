---
title: "wx小程序开发笔记-<button/>组件"
description: "介绍<button/>按钮组件的使用"
date: "2025-11-24"
tags: ["微信小程序", "button"]
---
:::attention
##### 1.基于 [微信官方文档-小程序-button](https://developers.weixin.qq.com/miniprogram/dev/component/button.html)
##### 2.在js+基础模板中使用。
:::
# 一、基础使用
### 1.创建按钮
```html
<button 
    //独有属性
    type="primary" //按钮类型
    loading='true' //名称前是否显示加载状态
    //通用属性
    disabled="true" //是否禁用按钮
    bindtap="handleTap" //点击事件绑定
    //事件参数
    data-value="123" //自定义参数，此为字符串
    data-index="{{123}}" //自定义参数，此为数字
    >
    点击我
</button>
```
# 二、基础事件
### 1.bindtap
```js
//点击事件绑定
handleTap(e){
    console.log(e.currentTarget.dataset.value);
    console.log(e.currentTarget.dataset.index);
}
```