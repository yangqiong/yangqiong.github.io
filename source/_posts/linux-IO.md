---
title: 文件IO和系统IO 
date: 2019-10-03 08:10:41
tags: Linux
---

* 文件I/O: 不带缓冲的I/O，每次read和write都调用内核的系统调用。
* 标准I/O：带缓存的I/O，目的是减少系统调用的次数。

## 标准I/O的缓冲类型

* 全缓冲
* 行缓冲
* 不带缓冲

默认惯例是标准错误stderr是不带缓冲的（使错误信息尽快显示出来），终端设备（比如console）使行缓存的，其他使全缓冲的。

碰到的一种情况是printf向标准输出打印（不带换行符），看不到标准输出输出内容。

```c
#include <stdio.h>

int main(){
  printf("Hello World");
  for (;;){

  }
  return 0;
}
```



解决办法：

1. ```printf("Hello World\n")```添加换行符打印（行缓冲）
2. ```fflush(stdout)```将缓冲区的数据清空到标准输出（刷新缓冲）
3. 如果是错误信息，写到标准错误也能立即显示`fprintf(stderr, "Hello World")`（不带缓冲）

## I/O效率

看使用场景，以及程序逻辑本身。

* 标准IO相对文件IO，不用人为关心缓冲区的大小，多数场景下减少了系统调用的次数，适用于常用场景。

* 文件IO可以控制一次性读取的大小，标准IO也可以调整缓冲区的设置。