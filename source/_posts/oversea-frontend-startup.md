---
title: 前端海外项目选型
date: 2022-07-23 16:20
tags: frontend, startup
---

# 前端海外项目选型

## 背景

- 出海团队，面向国际用户
- 管理端为主的数据产品

## 前端基础框架

前端主流三大框架`react`、`vue`、 `angular`都能满足前端基本需求。
所以更多的看团队成员配置和熟练度。
目前整个团队只有我一个前端且对`react`较熟悉，所以选择了`react`。

- 国内 angular 相对开发人员较少，所以基本不考虑
- UI 框架的选择有时会影响选择，比如`Element Plus`目前支持 vue3

## 前端构建工具

以`react`为基础的前端主流构建工具主要两个`vite`，`create-react-app`。
个人倾向选择`vite`。

1. 极致的本地开发体验。目前已经发布 3.0.0 相对已经成熟和稳定。
2. 根据之前开发经验，管理端项目后期往往包含大量页面，本地开发往往启动和编译很慢

## 前端 UI 组件库

倾向于`Ant Design`，国内最流行且组件库较为丰富。
相比较于`Element Plus`目前只支持 vue3,`Element UI`中 vue 和 react 样式不一致且开发团队主要以 vue 为主。
国外一些组件库比如`bootstrap`，`daisyui`等组件库偏 css 框架，组件库及功能较少

其他一些考虑点

- 支持主题配色
- 支持国际化

## 前端图表库

图标库的选择较多，有[Chart.js](https://www.chartjs.org/)，[ECharts](https://echarts.apache.org/zh/index.html)，[AntV.G2](https://g2.antv.vision/zh/)，[DataV](http://datav.jiaminghi.com/guide/)等国内外众多项目。
个人目前倾向于`Chart.js`，有插件能力支持。相对于只有属性修改适配，有更强的自定义能力。

## 前端播放器库

待考察

## 前端埋点上报

目前没找到专门针对前端的点击曝光等埋点的产品，更多的基于统计事件的上报和分析。
比如谷歌分析，GrowingIO，友盟等。那国外的话肯定使用谷歌分析。

## 前端国际化

- react-i18next ：通过多语言.json 配置文件的方式实现多语言
- react-intl：时间和货币等国际化显示
- 其他：一些自动化转换方案，目前看不完全成熟
- 动态数据的国际化，由后端翻译后直接传给前端。（待考察）

## 前端异常上报

目前想到的是`Sentry`可以基于 docker 进行搭建
