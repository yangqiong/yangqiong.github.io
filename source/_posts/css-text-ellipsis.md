---
title: CSS文本省略
date: 2019-09-22 11:04:36
tags: CSS
---

## CSS单行文本省略
```
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
```

## CSS多行文本省略
```
overflow: hidden;
text-overflow: ellipsis;
display: -webkit-box;
-webkit-box-orient: vertical;
-webkit-line-clamp: 2;
```