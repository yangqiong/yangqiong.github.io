---
title: 子元素水平垂直居中
date: 2020-02-12 19:07:36
tags: 
  - CSS
  - 前端面试题
---

#### 1.flex布局
```
.parent {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}
```

#### 2.transform偏移
```
.parent {
  position: relative;
}

.child {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

#### 3.margin偏移（如果子元素的宽度固定）
```
.parent {
  position: relative;
}

.child {
  position: absolute;
  top: 50%;
  left: 50%;
  margin-left: -50px;
  margin-top: -50px;
}
```