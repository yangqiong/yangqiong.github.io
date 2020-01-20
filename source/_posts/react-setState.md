---
title: React setState
date: 2020-01-20 16:02
tags: React
---

### 最佳实践

1. setState 不总是立即渲染组件，如果需要在 setState 后获取 this.state，应当在 setState callback 函数中或者在 componentDidUpdate 函数中（注：可能是合并 setState 再渲染之后的结果）
2. 如果想 setState 之后，用新的 state 再 setState，应使用第二种形式

### 两种形式

1. `setState({}, [, callback])`
2. `setState((state, props) => {return {}},[, callback])`

## 参考

- [react setState](https://reactjs.org/docs/react-component.html#setstate)
