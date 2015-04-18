---
layout: post
title: "AJAX POST&跨域之CORS"
modified:
categories: tech
excerpt:
tags: [JS]
image:
  feature:
  credit: 网络
  creditlink: javascript:;
---

<div id="cnblogs_post_body"><div>
<div>&#12288;&#12288;一晃又到新年了，于是开始着手好好整理下自己的文档，顺便把一些自认为有意义的放在博客上，记录成点的点滴。</div>
<div>&nbsp; &nbsp;&nbsp; <img alt="" src="http://images.cnitblog.com/blog/159097/201401/06081929-22224e37e3d54b0e95bf29b0c5de6919.gif"></div>
<div>&nbsp;</div>
<div><hr></div>
<div>&nbsp;</div>
<div>&#12288;&#12288;跨域是我在日常面试中经常会问到的问题，这词在前端界出现的频率不低，主要原因还是由于安全限制(同源策略， 即JavaScript或Cookie只能访问同域下的内容)，因为我们在日常的项目开发时会不可避免的需要进行跨域操作，所以跨域能力也算是前端工程师的基本功之一。</div>
<div>&#12288;&#12288;和大多数跨域的解决方案一样，JSONP也是我的选择，可是某天PM的需求变了，某功能需要改成支持POST，因为传输的数据量比较大，GET形式搞不定。所以折腾了下闻名已久的<strong>CORS（</strong>跨域资源共享，Cross-Origin Resource Sharing<strong>）</strong>，这边文章也就是折腾期间的小记与总结。</div>
<div>&nbsp; &nbsp;&nbsp; <img alt="" src="http://images.cnitblog.com/blog/159097/201401/06081959-ca75c7560afc42f1a52048bdcaad409a.jpg"></div>
<div>&nbsp; &nbsp; &nbsp;</div>
<div><hr></div>
<div>&nbsp;</div>
<h1>概述</h1>
<div>
<ul>
<li>CORS能做什么：</li>
</ul>
</div>
<div>&nbsp; &nbsp; &nbsp;正常使用AJAX会需要正常考虑跨域问题，所以伟大的程序员们又折腾出了一系列跨域问题的解决方案，如JSONP、flash、ifame、xhr2等等。</div>
<div>&nbsp; &nbsp; &nbsp;本文介绍的CORS就是一套AJAX跨域问题的解决方案。</div>
<div>&nbsp;</div>
<div>
<ul>
<li>&nbsp;CORS的原理：</li>
</ul>
</div>
<div>&nbsp; &nbsp; &nbsp;CORS定义一种跨域访问的机制，可以让AJAX实现跨域访问。CORS 允许一个域上的网络应用向另一个域提交跨域 AJAX 请求。实现此功能非常简单，只需由服务器发送一个响应标头即可。</div>
<div>&nbsp;</div>
<div>
<ul>
<li>CORS浏览器支持情况如下图：</li>
</ul>
</div>
<div>&nbsp; &nbsp; &nbsp;&nbsp; <img alt="" src="http://images.cnitblog.com/blog/159097/201401/06082033-9233ced009a644f9af909baca57a72b7.png" style="width: 760px;"></div>
<div>&nbsp; &nbsp;&nbsp; <img alt="" src="http://images.cnitblog.com/blog/159097/201401/06082103-f46e697e71884240b7200f8713697fbc.png"></div>
<div>&#12288;&#12288;喜闻乐见、普大喜奔的支持情况，尤其是在<strong>移动终端</strong>上，除了opera Mini；</div>
<div>&#12288;&#12288;PC上的现代浏览器都能友好的支持，除了IE9-，不过前端工程师对这种情况早应该习惯了...</div>
<div>&nbsp; &nbsp;&nbsp; <img alt="" src="http://images.cnitblog.com/blog/159097/201401/06082134-b13e1416aa0b453f89f71ad953807361.jpg"></div>
<div>&nbsp;</div>
<h1>CORS启航</h1>
<div>&nbsp;</div>
<div>&#12288;&#12288;假设我们页面或者应用已在<span>&nbsp;</span><span style="color: #0000ff;">http://www.test1.com</span>&nbsp;上了，而我们打算从<span>&nbsp;</span><span style="color: #0000ff;"><span style="color: #0000ff;">http://www.test2.com</span></span>&nbsp;请求提取数据。一般情况下，如果我们直接使用 AJAX 来请求将会失败，浏览器也会返回“源不匹配”的错误，"<span style="font-size: 19px; color: #6a0081;"><strong>跨域</strong></span>"也就以此由来。</div>
<div>&#12288;&#12288;利用 CORS，<span style="color: #0000ff;"><span style="color: #0000ff;">http://www.test2.com</span></span> 只需添加一个标头，就可以允许来自&nbsp;<span style="color: #0000ff;">http://www.test1.com</span> 的请求，下图是我在PHP中的 hander() 设置，<strong>“*”号表示允许任何域向我们的服务端提交请求</strong>：</div>
<div>&nbsp; &nbsp;&nbsp; <img alt="" src="http://images.cnitblog.com/blog/159097/201401/06082159-b1a102a3ce0e49e7841f76675236e408.png"></div>
&#12288;&#12288;<strong>也可以设置指定的域名，如域名<span>&nbsp;</span><span style="color: #0000ff;">http://www.test2.com</span>&nbsp;，那么就允许来自这个域名的请求</strong>：
<div>&nbsp; &nbsp;&nbsp; <img alt="" src="http://images.cnitblog.com/blog/159097/201401/06082227-10f22c4f75094faeb78255509199aed5.png"></div>
<div>&nbsp; &nbsp; &nbsp;</div>
<div>&#12288;&#12288;当前我设置的header为“*”，任意一个请求过来之后服务端我们都可以进行处理&amp;响应，那么在调试工具中可以看到其头信息设置，其中见红框中有一项信息是“<span style="font-size: 16px; color: #800080;"><strong>Access-Control-Allow-Origin：*</strong></span>&nbsp;”，表示我们已经启用CORS，如下图。</div>
<div>&#12288;&#12288;<span style="font-size: 13px;">PS：</span><span style="font-size: 13px;">由于demo都在我厂的两台测试机间完成，外网也不能访问，所以在这就不提供demo了，见谅</span><img alt="" src="http://images.cnitblog.com/blog/159097/201401/06082301-706148cc7ee142898b8eb25fcd62c406.jpg">
<div>&nbsp; &nbsp;&nbsp; <img alt="" src="http://images.cnitblog.com/blog/159097/201401/06082242-c70a37f237ed48c4a60d33fccfd467fb.png"></div>
<div>&nbsp;&#12288;&#12288;简单的一个header设置，一个支持跨域&amp;POST请求的server就完成了:)</div>
<div>&nbsp;</div>
<div>&#12288;&#12288;当然，如果没有开启CORS必定失败的啦，如下图：</div>
<div>&#12288;&#12288;<img alt="" src="http://images.cnitblog.com/blog/159097/201401/06110611-953e174761e545ad94da63fceee9afb4.jpg" style="width: 760px;"></div>
<h1>问题&amp;小结</h1>
<ul>
<li>刚刚说到的兼容性。CORS是W3C中一项较新的方案，所以部分浏览器还没有对其进行支持或者完美支持，详情可移至 <a target="_blank" href="http://www.w3.org/TR/cors/">http://www.w3.org/TR/cors/</a></li>
<li>安全问题。CORS提供了一种跨域请求方案，但没有为安全访问提供足够的保障机制，如果你需要信息的绝对安全，不要依赖CORS当中的权限制度，应当使用更多其它的措施来保障，比如OAuth2。</li>
</ul>
<div>
<div style="color: #000000; font-family: 微软雅黑; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: normal; orphans: 2; text-align: -webkit-auto; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px; font-size: medium;">
<div>&nbsp;</div>
<div>&#12288;&#12288;自认为的cors使用场景：</div>
<div>
<ul>
<li>cors在移动终端支持的不错，可以考虑在移动端全面尝试；PC上有不兼容和没有完美支持，所以小心踩坑。当然浏览器兼容就是个伪命题，说不准某个浏览器的某个版本就完美兼容了，说不准就有点小坑，尼玛伤不起！～</li>
<li>jsonp是get形式，承载的信息量有限，所以信息量较大时CORS是不二选择；</li>
<li>配合新的JSAPI(fileapi、xhr2等)一起使用，实现强大的新体验功能。</li>
</ul>
</div>
</div>

<div style="color: #000000; font-family: 微软雅黑; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: normal; orphans: 2; text-align: -webkit-auto; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px; font-size: medium;"><strong>&#12288;&#12288;祝2014顺利。</strong></div>
<div style="color: #000000; font-family: 微软雅黑; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: normal; orphans: 2; text-align: -webkit-auto; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px; font-size: medium;">&nbsp;</div>
<div style="color: #000000; font-family: 微软雅黑; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: normal; orphans: 2; text-align: -webkit-auto; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px; font-size: 24px;"><strong>参考资料:</strong></div>
<div style="color: #000000; font-family: 微软雅黑; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: normal; orphans: 2; text-align: -webkit-auto; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px; font-size: medium;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<span>&nbsp;</span><a target="_blank" href="http://www.w3.org/TR/cors/">http://www.w3.org/TR/cors/</a></div>
<div style="color: #000000; font-family: 微软雅黑; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: normal; orphans: 2; text-align: -webkit-auto; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px; font-size: medium;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<a target="_blank" href="http://www.html5rocks.com/en/tutorials/cors/">http://www.html5rocks.com/en/tutorials/cors/</a></div>
<div style="color: #000000; font-family: 微软雅黑; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: normal; orphans: 2; text-align: -webkit-auto; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px; font-size: medium;">&nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<a target="_blank" href="http://caniuse.com/#search=cors">http://caniuse.com/#search=cors</a></div>
<div style="color: #000000; font-family: 微软雅黑; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: normal; orphans: 2; text-align: -webkit-auto; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px; font-size: medium;">&nbsp;</div>
<div style="color: #000000; font-family: 微软雅黑; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: normal; orphans: 2; text-align: -webkit-auto; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px; font-size: medium;">&nbsp;</div>
</div>
</div>
</div></div>
