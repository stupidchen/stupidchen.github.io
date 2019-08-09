---
layout: post
title:  "关于Javascript中的Promise"
date:   2019-07-13 22:03:00 +0800
categories: [note, javascript, async]
---

# 前言

作为一个1/3吊子的前端工程师，对Javascript的了解局限于jQuery的我，初看到Promise时并没有觉得有什么不同之处。

# 概念简述 

Promise是一个类，它的构造函数仅接受一个双参数的函数。听起来有点拗口，我们看看下面的例子：

```
var promise = new Promise(function(resolve, reject) {
  // do a thing, possibly async, then…

  if (/* everything turned out fine */) {
    resolve("Stuff worked!");
  }
  else {
    reject(Error("It broke"));
  }
});
```

在这里，我们可以在匿名函数里干任何事情（比如说发送一个ajax请求）。在Promise被构造完后，匿名函数会被立即执行。这个时候我们相当于执行了以下代码：

```
function(resolve, reject) {
  // do a thing, possibly async, then…

  if (/* everything turned out fine */) {
    resolve("Stuff worked!");
  }
  else {
    reject(Error("It broke"));
  }
} (resolve, reject);
```

这看起来跟回调函数很像。但不同点在于，这里的resolve和reject两个函数都是**预先定义**好的。当你在匿名函数中调用resolve()或reject()时，会引起Promise自身的属性变化（如下图所示）。Promise有两个核心属性：

* state: 状态，取值为pending/fulfilled/rejected
* result: 返回值，初始值为undefined

![state](https://javascript.info/article/promise-basics/promise-resolve-reject@2x.png)

说到这你可能会发现，在匿名函数中我们并没有做消费。


但Promise的作用就在于，**then(resolve, reject)**的返回值同样也是一个Promise，这个Promise的工厂函数是这样的：

```
function generatePromise(retVal) {
  return new Promise(function(resolve, reject) {
                       try:
			             resolve(retVal);
                       catch:
                         reject(Error("It broke"));
			         });
};
```




# 总结

# 参考文档

* [Promise](https://javascript.info/promise-basics)
* [JavaScript Promises: an Introduction](https://developers.google.com/web/fundamentals/primers/promises)
