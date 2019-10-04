---
title: Linux 错误处理
date: 2019-10-04 08:22
tags: Linux
---

* UNIX系统函数出错时，通常返回一个负值，而且整形变量errno通常被设置为具体特定信息的值。
* 另外存在一些函数，在出错时会返回一个null指针。

## errno

1. 如果没有出错，其值不会被例程清除。因此仅当函数返回值指名出错时，才验证其值。
2. 任何函数都不会将errno设置为0。

### 打印错误信息

```c
char *strerror(int errnum); // 返回errno对应的出错消息字符串
```

```c
void perror(const char *msg); // 基于当前errno的值，在标准输出上产生一条错误信息。
															// 输出格式[msg: errno对应出错消息\n]
```

