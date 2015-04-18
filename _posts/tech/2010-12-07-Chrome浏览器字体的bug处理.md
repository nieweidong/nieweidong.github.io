---
layout: post
modified:
categories: tech
excerpt:
tags: [Chrome]
image:
  feature: post/chrome.jpg
  credit: 网络
  creditlink: javascript:;
---

　　作为WEB开发者我们得知道，看似简单的网页制作，如果要做得更好、更专业，真的是不简单。

　　我今天在A号机器上用chrome打开一个网页，再用B号机器上用chrome打开相同的网页，结果出现字体显示的太小不一样。原因是在简体中文版一直存在最小字体 12px 的限制。12px 有什么好处？就是别让字体太小，看着能舒服一点。

　　![](http://pic002.cnblogs.com/images/2010/159097/2010120719122214.jpg)

　　说实话，我不知道这是 Chrome 的 bug，还是 中文版Chrome 浏览器故意造成的，还是怕用户看不清 12px 以下的字号吗？蛋定...

　　其实解决它的最好方法仅仅只需要在你要写的css里面加上:-webkit-text-size-adjust:none;

　　好了，第一次写文章，欢迎大家拍砖。

