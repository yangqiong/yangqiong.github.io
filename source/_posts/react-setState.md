---
title: React setState
date: 2020-01-20 16:02
tags: React
---

### 两种形式

1. `setState({}, [, callback])`
2. `setState((state, props) => {return {}},[, callback])`

### 最佳实践

1. setState 不总是立即渲染组件，如果需要在 setState 后获取 this.state，应当在 setState callback 函数中或者在 componentDidUpdate 函数中（注：可能是合并 setState 再渲染之后的结果）
2. 如果想 setState 之后，用新的 state 再 setState，应使用第二种形式

### 注意

1. 经实际例子，在普通 componentDidmount 中，setState 之后不能立即通过 this.state 获取最新值；但是在异步流程中比如 setTimeout 可以。但是不管什么场景，应把 setState 当做异步来看待。

## 参考

- [react setState](https://reactjs.org/docs/react-component.html#setstate)
