---
layout: post
title: "「标准」的 JS风格"
modified:
categories: [tech, gonglue]
excerpt:
tags: [pattern, 前端攻略, Atom, Tools]
image:
  feature: banners/Lake Geroldsee, Germany.By Tatiana Pesotskaya.jpg
  credit: By Tatiana Pesotskaya
  creditlink: javascript:;
---

首先，这份 JS风格指南已经在我司的前端团队实行半年多了；  
其次，在程序员的世界里，从入行到资深都需要面对几个世界级的难题，如：

1. 世界上最好的编辑器是什么？
2. 是用空格还是 TAB？用空格还特么衍生出 2空格 VS 4空格。
3. JS到底要不要写分号？
4. ...

最后，PHP是世界上最好的语言。

![](http://www.fefork.com/images/em/xiaorentou/95.png)


### 一、规范VS自由
---

对程序员的每个个体来说，有代码规范其实不一定是好事，因为肯定会影响到写码的自由。  
比如某程序员习惯用 Tab，团队引入了某规范说都要换成 Spaces，这对于 Tab党来说这不是“噩耗”么。

尤其是对于老程序员，如果习惯多年的代码风格需要改变(先且不论好坏)，确实是件很拧巴的事情。

但是对整个团队来说，有代码规范肯定是大好事。而且由于好处实在太多，比如方便管理、好维护、易阅读等等，所以我也别一条条去罗列了，大家都懂:)

如果，某套代码规范甚至代码流程，能让团队中的成员都相对满意，而且还能切实的去执行...我想说：请好好珍惜这美好的时光。  
![](http://www.fefork.com/images/em/jinguanzhang/54.gif)

目前，各个大厂、各种开源项目都有多种 JS的写法规范。今天本文介绍的 JS 规范号称“Standard Style”，绝对是使用最广的写法之一(star 7800+)，而且有提供配套的工具、插件可以方便的使用。


### 二、介绍“JS Standard Style”
---

standardjs就是这个这个项目的名称。  
对了，它的作者叫 Feross，建议程序员们去了解一下，你会知道程序员世界的“猛人”到底能有多凶残。  
![](http://www.fefork.com/images/em/xiongmao/67.jpg)

请仔细看看这篇 JS规范要点，The Rules：

- ***2 spaces*** – for indentation
- Single quotes for strings – except to avoid escaping
- No unused variables – this one catches tons of bugs!
- ***No semicolons*** – It's fine. Really!
- Never start a line with (, [, or `
- This is the only gotcha with omitting semicolons – automatically checked for you!
- Space after keywords if (condition) { ... }
- Space after function name function name (arg) { ... }
- Always use === instead of == – but obj == null is allowed to check null || undefined.
- Always handle the node.js err function parameter
- Always prefix browser globals with window – except document and navigator are okay
- Prevents accidental use of poorly-named browser globals like open, length, event, and name.
- And more goodness – give standard a try today!

没错，先不管这个规范带来了多大的好处和优点，但是我标注的两个条件确实有点要命：**没有分号；2空格**。

有关是否有分号的讨论可以写许多篇论文了；  
至于用 tab还是用空格...都可以引发程序员的圣战啦。

所以这里看看就好，想了解更多的同学，强烈建议你私下去搜索些更多资料。ps：为毛要私下搜索？请参考下图，我其实只是想为你的安全考虑:)  
![](http://www.fefork.com/images/em/jinguanzhang/40.jpg)


### 三、先简单用起来！
---

官方的 demo 是使用 npm script 来展示的。
一句话表述：先全局安装  standard这个包，然后使用 CLI是实现后续的操作和展示。

> $ npm install standard --global

这种方式很适合用作 JS代码的校验审核。如下图：  
![](http://www.fefork.com/images/post/standardjs/s.png)

但是如果想配合日常开发用上，达到自动提醒，甚至自动格式化的程度，我非常推荐配合着对应的编辑器插件来使用。


### 四、配合编辑器插件
---

我喜欢和推荐这个规范的主要原因就是 —— 不用配置！  
ps：如果你有了解过 ESLint，面对那各种各样的 Configuring 和 Rules，特么有几个人能坚持去看完的，反正我是放弃了。  
![](http://www.fefork.com/images/em/xiaorentou/157.png)

但是使用 standardjs，它已经把规则都定好了，所以如果你接受它的规则，那么直接无脑使用就行了。如下图：  
![](http://www.fefork.com/images/post/standardjs/eslint.png)

支持 standardjs插件的编辑器还是很多的，几乎前端常用的编辑器都覆盖到了：  
  **Sublime Text、Atom、Vim、Emacs、Brackets、Visual Studio Code、WebStorm/PhpStorm。**

篇幅有限，仅介绍下在 Atom编辑器下的使用和效果吧。Atom需要安装对应的两款插件：

- linter-js-standard - Linter plugin for JavaScript Standard Style
- standard-formatter - Format file contents using JavaScript Standard Style

效果如下图：  
![](http://www.fefork.com/images/post/standardjs/standard-formatter.gif)

啊~这是个美好的时代。


### 五：如何在项目中实现统一的代码风格
---

不是每个程序员都有代码洁癖，也不是每个程序员都偏执的想写好代码，更多的普通人其实只是想少折腾的把工作完成就好。  
所以对于在团队内推行代码规范这种事情，顺其自然就好。

但是，使用以下这套方案可以让这套规范推行的更顺畅些。

第一步：项目中使用 ESLint，安装对应的包：

- eslint
- eslint-config-standard
- eslint-plugin-promise
- eslint-plugin-standard

![](http://www.fefork.com/images/post/standardjs/dev.png)

第二步：编辑器安装对应插件，以 Atom举例：

- linter-js-standard
- linter
- linter-eslint
- standard-formatter

最后一步：在项目中增加的 .eslintrc，只需要一行即可

> extends: standard

开发时自动格式化就这么实现了，想想是不是还有点小激动呢。  
**ps：希望你有颗包容的心，因为在这半年来，我们也确实遇到了一些小问题，善用 stackoverflow 和开源项目对应的 Issue，各种问题你都能找到答案。**


### 六、小结：聊几句优、缺点
---

对着这套 JS规范本身，一直都在泛泛而谈，优点和缺点的论述到处散落着，我在这简单梳理下我个人理解吧。

有关优点：

- **阅读代码的心情会变好** - 工作年限越长越能理解这句话的含义，这也是我最在意的一点，谁会有好心情去读第一眼糟糕的代码；更没有人愿意去读一个几百行，但是有几套代码风格的代码。
- 不用学习麻烦的 ESLint，无配置。
- 规范中有一条“No unused variables”没有细说，但确实非常有用。未使用的变量会进行提示，方便你优化、缩减代码，甚至定位问题。
- 想一想，如果团队有新人加入，不用过于担心他的代码风格了，不管他的工作年限。
- 有套路、好维护。

有关缺点：

- 如果对“JS Standard Style”的某条规范有异议，能否去修改呢？答：不能。
- 会影响少数人自由。单方面会冒犯到其他程序员，比如 Tab党、4空格党。
- 我们全团队使用 Atom，配合着对应的插件，偶尔会有点小问题。万能的 stackoverflow 和Issue 会帮助到我们。
- 对了，别被这套规范的名称给骗了，这其实不是真正的 JS标准，真正的 JS标准现在还在讨论的没玩没了呢。

以上就是我使用这套规范的感受吧。

最后，感谢已经离职的、优秀的德森同学(阿里花名“全栈”，我就问你们怕不怕)。是他强行在我们的 Nodejs Docker项目里面加上了这套玩意，让我们不得不用上了，哈哈哈哈哈哈哈哈。

这篇文章确实有点长了，那么再长点也无所谓了吧，于是我找到了下面这幅图...


### 七、看图，讲一个悲伤的故事
---

如果你没有尴尬癌，强烈推荐你看这个图片的出处 —— 《硅谷》。  
真的很多搞笑的点只有程序员才能正确 Get。

![](http://www.fefork.com/images/post/standardjs/space_vs_tab.jpg)

就这样，over.
