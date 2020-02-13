---
title: CSS样式层叠顺序
date: 2020-02-12 19:07:36
tags: 
  - CSS
  - 前端面试题
---

1. 当non-positioned原色（值不是relative,absolute,fixed等）和z-index（当然就很可能就不会出现重叠情况），根据元素出现的顺序。

2. 当涉及positioned元素（值为relative,absolute,fixed等）,显示在non-positioned元素前面。

3. z-index只在positioned元素生效（且在同级别元素比较）

## 参考
* [What No One Told You About Z-Index](https://philipwalton.com/articles/what-no-one-told-you-about-z-index/)
* [css-tricks z-index](https://css-tricks.com/almanac/properties/z/z-index/)