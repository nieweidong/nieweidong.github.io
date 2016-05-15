---
layout: post
title: "gulp使用小结(二)"
modified:
categories: tech
excerpt:
tags: [pattern, 前端攻略, Gulp, gulpjs]
image:
  feature:
  credit: 网络
  creditlink: javascript:;
---

接上篇文章接[gulp使用小结(一)](http://www.fefork.com/gulp_1/)

简单说说这篇文章我要说什么吧：

首先，[gulp-demos](https://github.com/nieweidong/gulp-demos)已经提交了个较通用的栗子。琢磨半天，原本准备分阶段搞些 ```gulp``` 套路，但是写完一个栗子之后，觉得当前这个栗子已经覆盖绝大多数的场景了。当偶偷懒，就酱...

然后，再一起看看这篇值得思考的文章《我为何放弃Gulp与Grunt，转投npm scripts》
[上](http://www.infoq.com/cn/news/2016/02/gulp-grunt-npm-scripts-part1)
[中](http://www.infoq.com/cn/news/2016/02/gulp-grunt-npm-scripts-part2)
[下](http://www.infoq.com/cn/news/2016/02/gulp-grunt-npm-scripts-part3)；

> 英文原文地址：[《Why I Left Gulp and Grunt for npm Scripts》](https://medium.freecodecamp.com/why-i-left-gulp-and-grunt-for-npm-scripts-3d6853dd22b8)

最后，漫谈下对前端构建工具的理解。

## 聊聊《npm scripts》

> 第一次阅读这篇就引起了我很多共鸣，因为在工作中处理的事务较杂，所以工作中没有过多的倾向性，神马好用就用神马。那么刚好 ```npm scrpts``` 和 ```gulp``` 都是偶常用的解决问题的方法。

这篇文章在 ```InfoQ``` 上被分成了三篇。

- 第一篇是埋汰 ```Gulp``` 和 ```Grunt```，各种不满意
- 第二篇开始描述 ```npm scripts``` 是如何强大和好理解
- 第三篇作者吐了下苦水，分享自己 ```npm scripts``` 带来的问题


“谈到了他对于Gulp、Grunt与npm scripts的认识，并且认为在现在的工程中，我们完全可以抛弃Gulp与Grunt，使用npm scripts就可以满足项目之所需。”

“众所周知，Gulp与Grunt是很多项目所使用的构建工具，他们也拥有非常丰富的插件。不过，我却认为Gulp与Grunt是完全不必要的抽象，npm scripts更加强大，并且更易于使用。”

那篇文章作者在上一个项目中遇到的问题：
1. gulpfile有100多行
2. 插件文档不重复
3. 某插件存在奇怪的bug
4. 某插件输出到命令行时丢失了颜色

但是，直接使用这些插件，所有问题都不复存在了。

npm scripts本身其实是非常强大的。https://docs.npmjs.com/misc/scripts#description




不说 ```npm start``` 和 ```npm run test``` 这种生存技能，在我司 ```Node``` 项目中，测试环境的上线与回滚，生产环境的上线与回滚，甚至某些后门代码都是依赖 ```npm scripts``` 搞定


## 借鉴


## 漫谈前端构建



这俩篇文章加上[gulp-demos](https://github.com/nieweidong/gulp-demos)，也算是自己对 ```Gulp``` 技术的一个总结:)
