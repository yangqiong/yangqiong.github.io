---
title: 可变参数
date: 2019-10-04 09:31
tags: C语音
---

宏可以接受可变数量的参数，所以可变参数函数是通过宏来实现的。

## 创建可变参数函数

1. 可变参数函数，至少需要一个形参和一个省略号```...```

2. 创建一个va_list类型的变量

3. 通过va_start初始化va_list，其中第二个变量最后一个命名形参的名称

4. 通过va_arg迭代访问形参，其中第二个变量为参数类型

5. 通过va_end完成清理工作。

## 局限性

1. 无法直接获取可变参数个个数
2. 需要知道可变参数的数据类型，使用用va_arg获取形参的时候需要在第二个参数指定

处理办法：

1. 最好一个命名形参传入可变参数数量，并且可变形参为同一类型
2. 可变形参为同一类型，最后一个可变形参为某种特殊约定
3. 类似printf，用最后一个可变形参，通过某种方式描述了可变形参的类型，并且其实间接指名了个数

## 例子

来源：https://linux.die.net/man/3/va_start

```c
void foo(char *fmt, ...)
{
    va_list ap;
    int d;
    char c, *s;

    va_start(ap, fmt);
    while (*fmt)
        switch (*fmt++) {
        case 's':              /* string */
            s = va_arg(ap, char *);
            printf("string %s\n", s);
            break;
        case 'd':              /* int */
            d = va_arg(ap, int);
            printf("int %d\n", d);
            break;
        case 'c':              /* char */
            /* need a cast here since va_arg only
               takes fully promoted types */
            c = (char) va_arg(ap, int);
            printf("char %c\n", c);
            break;
        }
    va_end(ap);
}
```

