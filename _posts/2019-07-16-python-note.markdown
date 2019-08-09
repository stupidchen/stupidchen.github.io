---
layout: post
title:  "Python知识点笔记"
date:   2019-07-13 22:03:00 +0800
categories: [note, python, advance]
---

* [Python Metaclasses](https://realpython.com/python-metaclasses/): 关于metaclass的意义和用法
* [Stabbing yourself with a fork() in a multiprocessing.Pool full of sharks](https://codewithoutrules.com/2018/09/04/python-multiprocessing/): 趣文，提出了一个关于Python自带进程池的假死bug。重点：了解Pool Worker的三种创建方式：Fork、Spawn、Forkserver
* [What's the difference between MySQLdb, mysqlclient and MySQL connector/Python?](https://stackoverflow.com/questions/43102442/whats-the-difference-between-mysqldb-mysqlclient-and-mysql-connector-python): 这个问答比较了Python中常用的三种mysql连接库的区别。个人总结：尽量多用PyMySQL，尽管mysqlclient有性能优势
