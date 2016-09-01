---
layout: post
title: "Linux 软件篇"
modified:
categories: [tech, gonglue]
excerpt:
tags: [Tools, Mac, Linux]
image:
  feature:
  credit: 网络
  creditlink: javascript:;
---

** 文章内容来着我整理的[fetool](https://github.com/nieweidong/fetool)，以下内容可能更新不及时 **

> 作为一名程序员兼工具控，我期待自己无比高效

首先，都是免费哒；然后，所列项目都是针对 ```CLI(命令行界面)``` 哒；最后，探索无止境

- [oh-my-zsh](http://ohmyz.sh/) - ___终端党___ 必用的好工具，强烈推荐
- [spf13-vim](https://github.com/spf13/spf13-vim) - 对于 Vim 偶之前做了好多文档和记录，但是自从了解有这个套路，那些记录都可以丢掉了。不过建议想了解的去看看 .vimrc 中的 Plugin，确实足够大而全。PS：如果遇见 ```neocomplete does not work``` 之类的错误，可以参考 [Problems with Vim and lua?](http://stackoverflow.com/questions/26724859/problems-with-vim-and-lua)
- [Vundle](https://github.com/VundleVim/Vundle.vim) - Vim 党必备。用于管理各种 Vim 插件，有 Git 就可以安装 ```$ git clone https://github.com/gmarik/vundle.git ~/.vim/bundle/vundle```
- [tree](http://mama.indstate.edu/users/ice/tree/) - linux 以树状图逐级列出目录的内容，装逼效果和实用功能都不错
- [cloc](http://cloc.sourceforge.net/) - 可用来计算 文件夹中各种语言的代码占比情况。展示内容非常直观，如某目录下 ```JavaScript``` 有多少个文件，共多少空格行数、注释行数、代码行数，就这些简单粗暴的内容。常见的安装方式可通过 ```npm``` 来进行安装。
- [oneapm](http://www.oneapm.com/) - 强大的运维工具，提供多种监控客户端； 有采集、分析、展示等一套功能； PS：我这用了服务器监控(免费哦)
- [httpie](https://github.com/jkbrzt/httpie) - 一个 CLI 中的 HTTP 客户端，用法简单，非常适合用来搞调试、测试
- [ESLint](http://eslint.org/) - 前端大神[Nicholas C. Zakas](http://nczonline.net/)创建。JavaScript 辅助编码的规范工具，有效控制偶们的代码质量
- [Lucario](https://github.com/raphamorim/lucario) 暗色系主题，支持 Vim, Atom, Sublime Text, TextMate, Terminal.app, iTerm, Xcode and XTerm
- [cmatrix](http://www.asty.org/cmatrix/) - 作用就是装逼，可以在屏幕上显示经典的黑客帝国的数码雨效果(看官方文档上也有其他效果，俺就不往细研究了)。在 Mac 下安装非常简单，一步搞定：`$ brew install cmatrix`

**Mac**
- [Homebrew](http://brew.sh/) - 有了他 ```OS X``` 程序猿能更好的专注代码层面。最近在看《七周七语言》，里面出现各种语言环境，用 ```brew``` 来安装、管理各种解释器和编译器，省心省力！
- [Xcode](https://developer.apple.com/xcode/) - 因为玩 ```Swift``` 所以早早就下载了，后来才知道原来 ```Mac``` 下如果不安装 ```Xcode```，部分常用的指令都不支持，囧

over:)
