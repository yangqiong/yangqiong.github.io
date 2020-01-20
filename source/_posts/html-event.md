---
title: HTML事件机制
date: 2020-01-20 17:11
tags: HTML
---

一个元素被点击时会触发三个阶段

1. 事件捕获阶段（capturing）：从顶层元素到此元素查看是否有通过`addEventListener(,,useCapture=true)`进行注册，如果有的话执行注册函数
2. 查看自己是否有通过`addEventListener()`进行注册，如果有的话执行注册函数
3. 事件冒泡阶段（bubbling）：从此元素到顶层原色查看是否有通过`addEventListener(,,useCapture=false)`(默认为 false)进行注册，如果有的话执行注册函数

### 注意

1. `on事件`是发生在冒泡阶段
2. `on事件`优先执行
3. 如果有注册多个`addEventListener`按注册顺序优先执行
4. `stopPropagation`阻止冒泡，阻止该元素的祖先元素的监听函数执行
5. `stopImmediatePropagation`阻止冒泡，阻止该元素的其他监函数执行以及祖先元素

## 参考

- [Event order](https://www.quirksmode.org/js/events_order.html#link4)
- [EventTarget.addEventListener](https://developer.mozilla.org/zh-CN/docs/Web/API/EventTarget/addEventListener)
