---
title: Javascript 事件机制
date: 2020-01-25 17:10
tags: Javascript
---

Javascirpt 代码都是在单线程中执行的，当遇到事件回调则把事件回调函数放到执行队列中，以及 setTimeout, Promise.then 等其他异步事件。

### setTimeout 和 setInterval

- 遇到 setTimeout，则是一段时间后将回调函数插入到队列中
- 遇到 setInterval，从遇到时刻起每个一段时间将回调函数插入队列中，如果队列中已经有此回调函数，则不插入

### 宏任务（任务）和微任务

1. 当一个宏任务执行结束后，执行所有微任务
2. 执行所有微任务以及微任务产生的微任务，直到清空微任务队列
3. 再执行宏任务（如上）

- macrotasks: 主线代码，setTimeout, setInterval, setImmediate, requestAnimationFrame, I/O, UI rendering
- microtasks: process.nextTick, Promises, Object.observe, MutationObserver

总结：仅偏理论，实际允许参考 1 中 5 的例子，是执行了完队列中所有宏任务，才执行的微任务

## 参考

1. [这一次，彻底弄懂 JavaScript 执行机制](https://juejin.im/post/59e85eebf265da430d571f89)
2. [Difference between microtask and macrotask within an event loop context](https://stackoverflow.com/questions/25915634/difference-between-microtask-and-macrotask-within-an-event-loop-context)
