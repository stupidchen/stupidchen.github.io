---
layout: post
title:  "关于Python中的logger"
date:   2019-07-13 22:03:00 +0800
categories: [note, python]
---

# 前言

本文主要考察Python的自带logger及现有第三方logger的概念和异同点。假如你对于logger的概念有所了解，但是又对Python自身的logger有所疑问的话，你或许能在下文中找到答案。

# 原生logger 

## 核心概念

原生的logger库（logging）包含以下4个核心概念：

* logger: 日志API的抽象（平时调用的info()或debug()等方法都是logger的方法）。logger是带有继承关系的。
* handler: 日志记录的处理者，可以被logger关联。当用户调用logger的方法尝试打日志时，logger关联的handler会拿到日志内容并且做对应的处理（比如说输出到屏幕/文件）
* filter: 顾名思义，日志的过滤器。过滤器可以和logger/handler相关联，从而决定哪些日志应该被输出
* formatter: 日志的格式化器。对于要输出的日志，formatter会用设定好的格式包装日志（如加上时间或进程号）后输出

四者间的关系如下图所示：
```
+------+  1:n  +-------+  1:1  +---------+
|logger+-------+handler+-------+formatter|
+---+--+       +---+---+       +---------+
    |              |
    |1:n           |
    |              |
+---+--+       1:n |
|filter+-----------+
+------+
```

稍微不直观的地方是，一个logger和handler可以和多个filter相关联。这里应当将filter理解成一个条件，logger/handler处理的日志需要满足所有的条件（filter）才能被输出、

在logging库中，日志在这四者中以LogRecord类传递。一个日志的打印流程的数据流如下图所示：

![logging_flow](https://docs.python.org/2.7/_images/logging_flow.png)

注意，在上图中左侧Logger flow中，一旦日志被交由handler处理（Pass to handlers of current logger），就将进入到右侧Handler flow的第一个判断步骤（Handler enabled for level for LogRecord）。

## logger的继承

TODO

## 值得注意的细节

* 线程安全性（自带的handler会使用锁保证I/O的线程安全性），但在实现signal模块的handler中最好不要使用这些handler
* logging.LogRecord的属性值得细看
* logging的变量及函数命名使用驼峰命名法

# 第三方logger

以下是一些star数较多的第三方logger库。

|名称|star|优点|缺点|
|:--------|:----------|:---------------|:-------------|
|[logzero](https://github.com/metachris/logzero)|804|非常好用的logger。支持日志切割及完善格式化输出（包括颜色），同时支持Python 2及3。|缺点：以logger而不是handler作为抽象，很难在它的基础上实现更灵活的日志输出（如不同的日志级别输出到不同的文件中）。在多进程场景下，日志切割不准确。|



# 总结

仅考虑Python 2.7.X的话，并没有比较好的支持多进程日志切割的logger。

# 参考文档

* [Logging HOWTO](https://docs.python.org/2.7/howto/logging.html#logging-basic-tutorial)
* [Logging Cookbook](https://docs.python.org/2.7/howto/logging-cookbook.html#logging-cookbook)
