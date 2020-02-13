---
title: Promise执行顺序
date: 2020-02-13 10:12
tags: 
 - Javascript
 - 面试题
---

1. Promise构造函数会立即执行
2. Promise存在三种状态：pendding(初始状态)，fulfilled(操作成功)，rejected(操作失败)
3. resolve, reject不会阻塞，异步触发后续函数执行，只变更一次触发
4. Promise的then方法的参数期望是函数，传入非函数则会发生值穿透。

面试题
```
setTimeout(() => {
  console.log(1);
}, 0)

new Promise((resolve, reject) => {
  console.log(2);
  for (let i = 0; i < 1000; i++) {
    if (i === 999) {
      resolve();
    }
  }
  reject();
  console.log(3);
}).then(() => {
  console.log(4);
}).catch(() => {
  console.log(6);
})
console.log(7);
```

答案
```
2
3
7
4
1
```