---
layout: post
title: "聊聊Node异步"
modified:
categories: [tech, gonglue]
excerpt:
tags: [Nodejs, CodeAnalyse]
image:
  feature:
  credit: 网络
  creditlink: javascript:;
---

写 Node 总要面对回调黑洞（Callback Hell）的问题，不过今时不同往日，现在解决这个问题的方法有不少，这篇文章希望能帮你梳理和理解这些方法。

Promise

async/await

generator
co4.0之前使用的是generator；4.0(含)之后使用的是Promise

---

http://www.jianshu.com/p/b709747d125e - 生成器（Generator）

https://zhuanlan.zhihu.com/p/20908500 - 「大概可能也许是」目前最好的 JavaScript 异步方案 async/await

https://www.zhihu.com/question/25413141 - nodejs异步控制「co、async、Q 、『es6原生promise』、then.js、bluebird」有何优缺点？最爱哪个？哪个简单

Promise文档 - https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise

Node.js回调黑洞全解：Async、Promise 和 Generator - https://zhuanlan.zhihu.com/p/19750470


---
