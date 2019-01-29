---
layout: post
title:  "Python中的关于协程的语法演变"
date:   2019-01-23 19:21:44 +0800
categories: [note, python]
---

# 概述

这里推荐一篇文章：[HOW THE HECK DOES ASYNC/AWAIT WORK IN PYTHON 3.5?](https://snarky.ca/how-the-heck-does-async-await-work-in-python-3-5/)

与协程（coroutine）和生成器（generator）相关的PEP：

* [PEP-255](https://www.python.org/dev/peps/pep-0255/)
    引入generator的概念和yield关键字
* [PEP-342](https://www.python.org/dev/peps/pep-0342/)
    引入send()和yield expression，语法元素丰富后的generator更适合作为coroutine来使用
* [PEP-380](https://www.python.org/dev/peps/pep-0380/)
    引入yield from，generator delegation
* [PEP-492](https://www.python.org/dev/peps/pep-0492/)
    引入async和await关键字，使corountine和generator可以严格区分

未完待续

