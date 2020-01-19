---
title: React 生命周期
date: 2020-01-18 19:29
tags: React
---

基于 v16 之后的生命周期函数

[![](/images/react-lifecycle.png)](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

## 挂载时

- `contructor`：通常用户创建初始的 state，refs。
- `getDerivedStateFromProps`：（很少使用）根据初始 props 设置 state。
- `render`：渲染
- `componentDidMount`：
  1. 通常发起异步请求
  2. 基于 DOM 做一些操作
  3. 添加事件监听

### 更新时

- `getDerivedStateFromProps`：（很少使用）根据 props 更新 state。
- `shouldComponentUpdate`：通常用户性能优化，判断是否进行渲染。首次渲染或者 forceUpdate 时候不执行。
- `render`：渲染
- `getSnapshotBeforeUpdate`：通常用户查看当前 DOM 属性，以及传递值给 componentDidUpdate
- `componentDidUpdate`：通过用于对 DOM 进行操作，或者有条件的更新 state

### 卸载时

- `componentWillUnmount`：通过用于清理操作

### 错误

- `getDerivedStateFromError`：通过用于更新 state，从而渲染错误页面
- `componentDidCatch`：通常用于子组件错误的捕获和打印

## 参考

- [React 16 Lifecycle Methods: How and When to Use Them](https://blog.bitsrc.io/react-16-lifecycle-methods-how-and-when-to-use-them-f4ad31fb2282)
- [react-lifecycle-methods-diagram](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)
