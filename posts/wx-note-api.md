---
title: "微信小程序开发笔记-Api"
date: "2025-11-05"
description: "一些微信小程序的api介绍"
tags: ["微信小程序", "Api"]
img: "https://olist.negine.top/d/%E4%B8%AD%E5%9B%BD%E7%A7%BB%E5%8A%A8%E4%BA%91%E7%9B%98/%E6%89%8B%E6%9C%BA%E5%9B%BE%E7%89%87/background.webp?sign=hN9y0FEThdPycXoDbpGQh85kogBkXMDowjPibt6YII0=:0"
---

:::attention
##### 1.基于 [微信官方文档-小程序-api](https://developers.weixin.qq.com/miniprogram/dev/api/base/debug/RealtimeLogManager.html)
##### 2.在js+基础模板中使用。
:::


## 一、基础
### 1.wx.env

```js
//使用wx.env.USER_DATA_PATH获取文件系统中的用户目录路径 (本地路径)
this.setData({
            wx_env:wx.env.USER_DATA_PATH,
        })
//wx_env输出http://usr
```
### 2.wx.canIUse(string schema)

```js
//用于判断小程序的API，回调，参数，组件等是否在当前版本可用,返回true/false.
wx.canIUse('console.log')
```

### 3.wx.base64ToArrayBuffer(string base64)

```js del={1}
//已停止更新，不推荐使用
//将 Base64 字符串转成 ArrayBuffer (二进制)对象。

 const base64 = 'negine';
 const arrayBuffer = wx.base64ToArrayBuffer(base64);
```

### 4.wx.arrayBufferToBase64(ArrayBuffer arrayBuffer)

```js del={1}
//已停止更新，不推荐使用
//将 ArrayBuffer 对象转成 Base64 字符串

 const arrayBuffer = new Uint8Array([11, 22, 33])
const base64 = wx.arrayBufferToBase64(arrayBuffer)
```
## 二、路由
### 1.wx.switchTab(Object object)

```js
//跳转到 tabBar 页面，并关闭其他所有非 tabBar 页面
//支持SFC

wx.switchTab({
  url: '/index'
})
```
### 2.wx.rewriteRoute(Object object)

```js
//重写正在进行中的路由事件，推荐配合wx.onBeforeAppRoute()
//支持SFC
//preserveQuery选择是否保留参数，默认为false

//例如，我们可以通过这样的方式将所有跳转到页面 A 的路由都重写到页面 B：

// 添加路由事件处理前的监听
wx.onBeforeAppRoute(res => {
  // 监听触发时，判断事件是否需要重写
  if (res.path === '/pages/A/A') {
    // 重写路由事件
    wx.rewriteRoute({
      url: '/pages/B/B',
      preserveQuery:true,//保留参数
      success(res) {
        console.info('Rewrite successfully from A to B')
      },
      fail(res) {
        console.error('Rewrite failed, reason: ' + res.errMsg)
        // 由于兼容性问题或场景不适用等原因重写失败，回退
        wx.redirectTo({
          url: '/pages/B/B',
          complete: console.info
        })
      }
    })
    return
  }
})
```
### 3.wx.reLaunch(Object object)

```js
//关闭所有页面，打开到应用内的某个页面
//支持SFC

wx.reLaunch({
  url: 'test?id=1'
})

```

### 4.wx.redirectTo(Object object)

```js
//关闭当前页面，跳转到应用内的某个页面。但是不允许跳转到 tabbar 页面
//支持SFC

wx.redirectTo({
  url: 'test?id=1'
})//不能是tabbar

```
### 5.wx.navigateTo(Object object)

```js
//保留当前页面，跳转到应用内的某个页面。但是不能跳到 tabbar 页面。
//使用 wx.navigateBack可以返回到原页面。小程序中页面栈最多十层。
//支持SFC
//详见微信开发文档

wx.navigateTo({
  url: 'test?id=1'
})
```
### 6.wx.navigateBack(Object object)

```js
//关闭当前页面，返回上一页面或多级页面。
//可通过 getCurrentPages 获取当前的页面栈，决定需要返回几层。
//支持SFC

wx.navigateBack({
  delta: 2 //需要返回的页数
})

```


