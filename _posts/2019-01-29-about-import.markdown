---
layout: post
title:  "关于Python中的import的笔记"
date:   2019-01-29 18:01:01 +0800
categories: [note, python]
---

# 概述

相信写过Python的人或多或少都会使用过import关键字。常见的import关键字的使用方法有如下几种：

* ``import pkg``
* ``import pkg.mod``
* ``import pkg.mod.submod/clz/func``
* ``from pkg import mod``
* ``from pkg.mod import submod/clz/func`` 

在以上的例子里，pkg = package, mod = module, submod = sub module, clz = class, func = function

Python interpreter会通过__import__()来引入以上元素。

除此之外，还有以下几种方式可以实现**dynamic import**：

* import\_lib.import\_module
    封装了__import__()，针对relative import做了特殊处理

__import__()依赖于sys.path，sys.path由一系列的规则生成。

在所需要引入的目标不在sys.path中时，可通过两种方式实现引入：

* 添加sys.path
* 使用Loader装载目标的源文件

# __all__

module文件夹下的__init__.py中的__all__仅在该module被import时起作用。

*未完待续*

