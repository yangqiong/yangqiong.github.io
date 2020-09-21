---
title: Tree Shaking
date: 2020-09-21 11:14
tags: 
 - Javascript
---

## 什么是Tree Shaking
Tree Shaking用于去除无用的代码。

## 为什么ES6 module之后出现了Tree Shaking
因为ES6 module引入模块的方式是静态（static）的。而CommonJS模块使用require语法可以动态引入模块
```
import foo from "foo";
import bar from "bar";

if (condition) {
    // do stuff with foo
} else {
    // do stuff with bar
}
```

```
var myDynamicModule;

if (condition) {
    myDynamicModule = require("foo");
} else {
    myDynamicModule = require("bar");
}
```

## 注意
* 如果代码包含`side effects`，但无导出，比如`polyfill`，需要通过配置标记


## 参考
* [https://bitsofco.de/what-is-tree-shaking/](https://bitsofco.de/what-is-tree-shaking/)