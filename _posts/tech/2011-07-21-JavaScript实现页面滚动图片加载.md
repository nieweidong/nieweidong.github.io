---
layout: post
modified:
categories: tech
excerpt:
tags: [JS]
image:
  feature:
  credit: 网络
  creditlink: javascript:;
---

　　又到了这个月的博客时间了，原计划是打算在这个月做一个的功能较炫的拖拽类，可是感觉想的太容易，实现起来遇见不少问题，如果技术分享做不到有助于人反而害人，那就歇菜了，所以还是等本人多找些资料研究研究，“拖拽类“先放放吧，下面开始正题...

　　为什么写这篇文章？

　　1.优化页面很实用的方法，技术实现不难；

　　2.搜索了相关内容的文章，好像都是用jQuery的方法，可是如果不用jQuery的站长难道就不能用这种方法了么；

　　3.做技术分享也是在让更多人帮自己测试，因为这个本人木有在项目中实际用到，都是自己琢磨的，所有如果有问题请大家指出，先谢谢了；

　　4.这个月的博客还没写；

　　5.刚好木有工作任务，此时不写更待何时...


　　现在的页面大多都具有的特点 - 内容丰富，图片较多；像我们经常浏览的淘宝，京东，团购网站之类的（本人网购控，属于一个月不在网上花点钱就不痛快），一个页面几十张图片那叫毛毛雨，所以现在流行起了一个方法 - 滚动动态加载。这个方法能解决很大程度的HTTP请求，首先页面只加载窗口显示区的图片，只有等到页面滚动，且滚动到相应位置的时候再去加载图片，这样做网页加载快了（请求少了，加载的东西少了能不提快么）。在高性能网站建设指南》第一章就说到，减少HTTP请求的重要性，这是提高网页前端性能，优化页面加载速度很实用的做法。


　　原理：

　　1.给页面绑定滚动事件；

　　2.加载页面的时候把真正的图片地址放在某属性中；

　　3.然后再滚动过程中判断元素是否进入当前浏览器窗口内；

　　4.最后加载图片，当然加载什么，用什哪种用户体验都得由你决定；


　　难点：

　　浏览器兼容是造成难点的原因所在，DOM标准和IE标准，每天前端的工作都在和它们打交道。思考下面的几段代码

> window.pageYOffset ? window.pageYOffset : window.document.documentElement.scrollTop

　　目的:获得当前页面相对于窗口显示区左上角的 Y 位置.

　　DOM标准:window.pageYOffset;

　　IE标准:window.document.documentElement.scrollTop

> window.innerHeight ? window.innerHeight : document.documentElement.clientHeight

　　目的:声明了窗口的文档显示区的高度和宽度，以像素计.

　　DOM标准:innerheight 和 innerwidth;

　　IE标准:document.documentElement 或 ducument.body （与 DTD 相关）的 clientWidth 和 clientHeight 属性作为替代

> obj.getBoundingClientRect().top + window.document.documentElement.scrollTop + window.document.body.scrollTop

　　目的:获取页面元素的位置.

　　当浏览器为 非webkit内核 时，document.body.scrollTop值恒定为0，使用 document.documentElement.scrollTop才能取到正确值 ;

　　当浏览器为 webkit内核 时，document.documentElement.scrollTop值恒定为0，使用 document.body;

　　我还搜索到一种说法是和DTD相关（即 当页面指定了 DOCTYPE时，使用 document.documentElement ; 当页面没有指定了 DOCTYPE时，使用 document.body），请确定知道的朋友帮忙指出下，不胜感谢。



　　细节：

　　1. 因为真正的地址最初是在某属性中(默认是xsrc，可自己设置)，所以默认的图片地址最好是一个像素的透明图片，这样可以避免在浏览器中出现红X；

　　2. 在图片load的时候可以加入等待的图片，这样用户才会知道这里有图片需要加载，良好的用户体验是前端一直所追求的(例子中有体现)；

　　3. 在图片load成功后可以加入合适的显示效果(例子中木有体现，可以自己尝试)；

---

JavaScript源码如下：

{% highlight javascript %}
var scrollLoad = (function (options) {
        var defaults = (arguments.length == 0) ? { src: 'xSrc', time: 300} : { src: options.src || 'xSrc', time: options.time ||300};
        var camelize = function (s) {
            return s.replace(/-(\w)/g, function (strMatch, p1) {
                return p1.toUpperCase();
            });
        };
        this.getStyle = function (element, property) {
            if (arguments.length != 2) return false;
            var value = element.style[camelize(property)];
            if (!value) {
                if (document.defaultView && document.defaultView.getComputedStyle) {
                    var css = document.defaultView.getComputedStyle(element, null);
                    value = css ? css.getPropertyValue(property) : null;
                } else if (element.currentStyle) {
                    value = element.currentStyle[camelize(property)];
                }
            }
            return value == 'auto' ? '' : value;
        };
        var _init = function () {
            var offsetPage = window.pageYOffset ? window.pageYOffset : window.document.documentElement.scrollTop,
                offsetWindow = offsetPage + Number(window.innerHeight ? window.innerHeight : document.documentElement.clientHeight),
                docImg = document.images,
                _len = docImg.length;
            if (!_len) return false;
            for (var i = 0; i < _len; i++) {
                var attrSrc = docImg[i].getAttribute(defaults.src),
                    o = docImg[i], tag = o.nodeName.toLowerCase();
                if (o) {
                    postPage = o.getBoundingClientRect().top + window.document.documentElement.scrollTop + window.document.body.scrollTop; postWindow = postPage + Number(this.getStyle(o, 'height').replace('px', ''));
                    if ((postPage > offsetPage && postPage < offsetWindow) || (postWindow > offsetPage && postWindow < offsetWindow)) {
                        if (tag === "img" && attrSrc !== null) {
                            o.setAttribute("src", attrSrc);
                        }
                        o = null;
                    }
                }
            };
            window.onscroll = function () {
                setTimeout(function () {
                    _init();
                }, defaults.time);
            }
        };
        return _init();
    });

    scrollLoad();

{% endhighlight %}

[demo下载](http://files.cnblogs.com/Darren_code/ScrollLoad.rar)

可传递一个参数设置src原地址和响应时间:

```
scrollLoad({
    src:'userSrc'， //字符串型
    time: 100       //数字型
})
```

最后，祝大家工作愉快，学习进步，哈哈..

