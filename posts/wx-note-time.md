---
date: '2025-11-20'
description: 如何在小程序中获取并计算时间
tags:
  - 微信小程序
  - 时间
  - 代码示例
title: 微信小程序开发笔记-计算时间
---

## 一、初始加载

```js
onLoad() {
   this.startTimer();//调用定时器
}

```

## 二、定时器

```js
startTimer(){
    //检查定时器是否存在
    if(this.timer) return;
    //想要计算的时间
    this.targetDate = new Date('2026-3-16T09:00:00UTC');
    //定义定时器
    this.timer = setInterval(() => {
        this._trackTime();//调用计算时间方法
    },1000)
}
```

## 三、计算时间

```js
//计算时间方法
_trackTime(){
    //获取当前时间戳
    const now = Date.now();
    //计算时间差，ms
    let diff = this.targetDate.getTime() - now;

    if (diff <= 0) {
      // 到达或超时，显示 0 并停止计时
      this.setData({
        days: '0',
        hours: '00',
        minutes: '00',
        seconds: '00'
      });
      this.stop();
      return;
    }

    // 转换为秒,向下取整
    let totalSec = Math.floor(diff / 1000);

    const days = Math.floor(totalSec / (24 * 3600));
    totalSec -= days * 24 * 3600;

    const hours = Math.floor(totalSec / 3600);
    totalSec -= hours * 3600;

    const minutes = Math.floor(totalSec / 60);
    const seconds = totalSec - minutes * 60;

    this.setData({
      days: String(days),
      hours: this._pad(hours),
      minutes: this._pad(minutes),
      seconds: this._pad(seconds)
    });
}
//补零方法
_pad(num) {
    return num < 10 ? '0' + num : String(num);
}
```
