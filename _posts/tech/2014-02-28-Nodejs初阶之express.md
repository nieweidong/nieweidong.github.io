---
layout: post
modified:
categories: [tech, gonglue]
excerpt:
tags: [Nodejs, 前端攻略]
image:
  feature:
  credit: 网络
  creditlink: javascript:;
---

<div id="cnblogs_post_body"><div><span style="font-family: 幼圆; font-size: 16px;"><span style="line-height: 1.5;">&#12288;&#12288;PS: 2014/09/24 更新《<a target="_blank" href="http://www.cnblogs.com/Darren_code/p/express4.html">Express 4.X 启航指南</a>》，欢迎阅读和评论:)</span></span></div>
<div>&nbsp;</div>
<div><span style="font-family: 幼圆; font-size: 16px;"><span style="line-height: 1.5;">&#12288;&#12288;</span><span style="line-height: 1.5;">老规矩，开头部分都是些自娱自乐的随想，想到哪写到哪...</span></span></div>
<div><span style="line-height: 1.5; font-family: 幼圆; font-size: 16px;">&#12288;&#12288;到今天俺已经在俺厂工作俩年零几天了，工作以来头一回在一家企业工作超俩年，对于这俩年确实只有满满的成就感，不管是工作还是生活...写到这句突然又想写篇这俩年的总结，等这篇文章发了之后就着手整理吧，吼吼。</span></div>
<div><span style="line-height: 1.5; font-family: 幼圆; font-size: 16px;">&#12288;&#12288;<img alt="" src="http://images.cnitblog.com/blog/159097/201402/262041577757011.gif"></span></div>
<div><span style="line-height: 1.5; font-family: 幼圆; font-size: 16px;">&#12288;&#12288;</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;"><span style="line-height: 1.5;">&#12288;&#12288;那篇《<a target="_blank" href="http://www.cnblogs.com/Darren_code/archive/2011/10/31/nodejs.html" title="node.js 初体验">node.js 初体验</a>》好像才发生在前几月，没想到时间已过两年有多。且看到文章末尾处那句： “这篇文章只会是一个开始” 令俺脸红掩面<img alt="" src="http://images.cnitblog.com/blog/159097/201402/270046481715808.gif">，尼玛真没想到这一开始就开始了两年</span>多，这让老夫情何以堪<img alt="" src="http://images.cnitblog.com/blog/159097/201402/270002525962790.gif">...</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288;好吧，反正脸皮厚已不是俩三天，让俺装傻混过去吧，咱往前看才是硬道理不是。俺一定痛改前非、洗心革面、好好改造，今年中心的小心思是把【<a target="_blank" href="http://www.cnblogs.com/Darren_code/archive/2013/01/05/fe_series.html">前端攻略系列</a>】折腾点名堂出来，厚积薄发的时刻来鸟。</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp;</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288;Node不得不写写，没辙呀，太火！看看最近的前端圈子吧，没弄过几行Node代码都不好意思和别人打招呼；不折腾点Node的小平台、小工具，去食堂都不好意思多搞几碗饭，所以俺也就顺大潮把自己的工作笔记整理整理，试试能否写好这篇Nodejs系列。</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288;<img alt="" src="http://images.cnitblog.com/blog/159097/201402/270010498417459.jpg"></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp;</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288;好吧，不开玩笑哒~~~介绍这篇和接下来几篇Node文章的内容，基本都属于Node的初阶，略偏实战，进阶和高阶内容正在YY中，最终的目录与里程碑下一篇应该差不多能定下来。</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288;本篇以介绍Express为话题，延伸出用Node开发小页面，然后其中穿插概述express主要的API、路由的原理、Node模块概念，顺便也会介绍自己使用Node工具等等。默认看官们都具备JavaScript基础，所以过于基础的内容俺就不浪费篇幅咯，GOGO。</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp;</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288;最后自我爆料一个吧。老婆已回家养胎，所以俺穷的只有时间了。有时间好好加班拼工作，有时间好好写博(客)拼积累...诸如心灵鸡汤什么的就不灌各位啦，喝多了反胃:)</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288;一不小心随想就写了那么多，尼玛炫酷狂拽屌炸天有木有！<br></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288;<img alt="" src="http://images.cnitblog.com/blog/159097/201402/271125378366371.gif"></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp;</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;"><em><span style="line-height: 1.5; color: #888888;">--------------------------------------------&nbsp;华丽丽的分割线 --------------------------------------------</span></em></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp;</span><br>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288;Node和NPM的安装够便捷了，不细说...有几点基础顺手提一下：</span></div>
<div><ol>
<li><span style="font-family: 幼圆; font-size: 16px;">安装命令中的 “-g” 表示全局(global)</span></li>
<li><span style="font-family: 幼圆; font-size: 16px;">express的版本不是通常的 “-v” 来查看，而是 “-V”</span></li>
<li><span style="font-family: 幼圆; font-size: 16px;">安装express项目的命令如下<br><strong><span style="background-color: #ffffff; color: #993366;">express -e nodejs-product</span></strong><br></span>
<div><span style="font-family: 幼圆; font-size: 16px;">-e, --ejs add ejs engine support <br></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">-J, --jshtml add jshtml engine support (defaults to jade)</span></div>
























<span style="font-family: 幼圆; font-size: 16px;">

PS：模板引擎之类暂时不必care，不过俺当初学习搭建Node+express时用的是ejs，所以也就顺手一直用着了</span></li>


























</ol></div>
<div>&nbsp;</div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp;</span></div>
<div>
<div><span style="font-family: 幼圆; font-size: 16px; background-color: #ccffff;">&#12288;&#12288;<span style="font-size: 18px;"><strong>Node的小基友supervisor&#12288;&#12288;</strong></span></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288;每次修改代码后会自动重启。懒程序员就指望这种省事省力的工具活着了:)</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288;安装：<span style="color: #993366;"><strong>npm install -g supervisor</strong></span></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288;执行：<span style="color: #993366;"><strong>supervisor app.js</strong></span></span></div>
























<span style="font-family: 幼圆; font-size: 16px;">

<strong><span style="color: #41007d;"><br></span></strong></span></div>
<div>
<div><span style="font-family: 幼圆; font-size: 16px; background-color: #ccffff;">&#12288;&#12288;另一个<span style="font-size: 18px;"><strong>小基友forever</strong></span></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288;虚拟机一关node服务就关了，不过forever可以让node服务不停止，介绍如下，安装和执行不细说啦，我懒：</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288;forever是一个简单的命令式nodejs的守护进程，能够启动，停止，重启App应用。forever完全基于命令行操作，在forever进程之下，创建node的子进程，通过monitor监控node子进程的运行情况，一旦文件更新，或者进程挂掉，forever会自动重启node服务器，确保应用正常运行。</span></div>


</div>
<div><span style="font-family: 幼圆; font-size: 16px;"> &nbsp;</span></div>
<div><span style="font-family: 幼圆; font-size: 16px; background-color: #ccffff;">&#12288;&#12288;<span style="font-size: 18px;"><strong>express项目目录&#12288;&#12288;</strong></span></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;<img alt="" src="http://images.cnitblog.com/i/159097/201402/272113409312155.png"></span></div>
<div>&#12288;&#12288;如<span style="font-family: 幼圆; font-size: 16px;">上图就是一个express项目结构，简单过一下：</span></div>
<div>
<ul>
<li><span style="font-family: 幼圆; font-size: 16px;">app.js： 项目入口，反正express爱叫app.js没辙，你可以改成index.js或者main.js都成。相当于php项目中的 index.php、index.html</span></li>
<li><span style="font-family: 幼圆; font-size: 16px;">node_modules： 存放项目的依赖库</span></li>
<li><span style="font-family: 幼圆; font-size: 16px;">package.json： 项目依赖配置及开发者信息(这个要说就说多了，还是看文档好，俺就不误人子弟了。下期看看抽个小段单说Node模块)</span></li>
<li><span style="font-family: 幼圆; font-size: 16px;">public： 静态文件如 css,js,img (PS:俺其实习惯叫static)</span></li>
<li><span style="font-family: 幼圆; font-size: 16px;">routes： 路由文件(学习的重要攻克对象。尼玛业务好不好，路由是关键)</span></li>
<li><span style="font-family: 幼圆; font-size: 16px;">Views： 页面文件(Ejs或者jade的模板，默认是jade，俺这用Ejs，在初阶练手最重要，所以都可以试试)</span></li>











































</ul>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;打开View 文件发现index.ejs比较不习惯，所以对app.js进行小改动：</span></div>











































</div>
<div><ol>
<li><span style="font-family: 幼圆; font-size: 16px;">“app.set('view engine', 'ejs');” 变成 “app.engine('.html', ejs.__express);app.set('view engine', 'html');”</span></li>
<li><span style="font-family: 幼圆; font-size: 16px;">上一行出现的ejs变量需要require ejs模块，增加代码“var&nbsp;ejs = require('ejs');”</span></li>











































</ol>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;最终的app.js如下：</span></div>











































</div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp;&nbsp; <img alt="" src="http://images.cnitblog.com/i/159097/201402/280037097683921.png"><br></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp;</span></div>
<div><span style="font-family: 幼圆; font-size: 16px; background-color: #ccffff;">&#12288;&#12288;<strong><span style="font-size: 18px;">代码小解：&#12288;&#12288;</span></strong></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;因为针对的是初阶入门，俺们还是继续过一下express的使用与Node的方法哈：</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;require() 用于在当前模块中加载和使用其他模块；此方法是模块的基础，使用中大概有路径的概念就行。PS：JS文件可以去掉".js"后缀</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288; exports 表示模块的导出对象，用于导出模块的属性和公共方法。在项目routes文件夹下有index.js和users.js（路由有细说），都使用到exports对象导出对象，如33行的routes.index和34行的user.list;<br></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288; PS：一个模块的代码只会在模块第一次被使用时执行，不会因require多次而被初始化多次。</span></div>
<div>&nbsp;</div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;<strong>express()&nbsp;</strong>表示创建express应用程序。简单几行代码其实就可以创建一个应用，如下：</span></div>
<div class="cnblogs_code"><div class="cnblogs_code_toolbar"><span class="cnblogs_code_copy"><a title="复制代码" onclick="copyCnblogsCode(this)" href="javascript:void(0);"><img alt="复制代码" src="http://common.cnblogs.com/images/copycode.gif"></a></span></div>
<pre>     <span style="color: #0000ff;">var</span> express = require('express'<span style="color: #000000;">);
     </span><span style="color: #0000ff;">var</span> app =<span style="color: #000000;"> express();
     app.get(</span>'/', <span style="color: #0000ff;">function</span><span style="color: #000000;">(req, res){
          res.send(</span>'hello world'<span style="color: #000000;">);
          console.log(</span>'hello world'<span style="color: #000000;">);
     });
     app.listen(</span>'8808');</pre>
<div class="cnblogs_code_toolbar"><span class="cnblogs_code_copy"><a title="复制代码" onclick="copyCnblogsCode(this)" href="javascript:void(0);"><img alt="复制代码" src="http://common.cnblogs.com/images/copycode.gif"></a></span></div></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;app.listen() 就是在给定的主机和端口上监听请求，这个和node中http模块的http.createServer(function(){...}).listen()效果一致；</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;app.set(name, value)和app.get(name)就是你想的那样，set()为设置 name 的值设为 value，get()为获取设置项 name 的值。如俺app.js的图片16行中的一句“app.set('port', process.env.PORT || 3000)”就是设置项目的port，在下面使用http.createServer时就可以使用app.get('port')来获取，只是俺偷懒没用来着<img alt="" src="http://images.cnitblog.com/i/159097/201402/280809248922088.gif">；</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;了解app.engine()方法之前先看看express应用的安装命令:“express -e nodejs-product”，其中的 -e 和 -J 我们一开始已经提到，表示ejs和jade模板。</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;如果想把模板后缀改成“.html”时就会用到app.engine方法，来重新设置模板文件的扩展名，比如想用ejs模板引擎来处理“.html”后缀的文件：app.engine('.html', require('ejs').__express);</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;app.engine(ext, callback) 注册模板引擎的 callback 用来处理ext扩展名的文件。</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288; PS：<span style="font-family: 幼圆; font-size: 16px;">__express</span>不用去care，其实就是ejs模块的一个公共属性，表示要渲染的文件扩展名。<br></span></div>
<div>&nbsp;</div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;app.use([path], function) 使用中间件 function,可选参数path默认为"/"。使用 app.use() “定义的”中间件的顺序非常重要，它们将会顺序执行，use的先后顺序决定了中间件的优先级(经常有搞错顺序的时候);</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp;</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;最后介绍个很有用的express API：</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;app.render(view, [options], callback)&nbsp;渲染 view, callback 用来处理返回的渲染后的字符串。</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;</span></div>
<div><span style="background-color: #ccffff;"><strong><span style="font-family: 幼圆; font-size: 18px;">&#12288;&#12288;路由实战：&#12288;&#12288;</span></strong></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp;&nbsp; 路径代码应该是项目中最本机的一部分了。express中创建一个或者一套新的handle非常简单，先看看express现有的，一会儿我们创建俩个实际的规则。</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp;&nbsp; <img alt="" src="http://images.cnitblog.com/i/159097/201402/282058558455441.png"><br></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp;&nbsp; 变量 routes 和 user 都是刚才require的模块，他们各自exports了index方法和list方法；其中<span style="font-family: 幼圆; font-size: 16px;">Response</span>.render()表示渲染view，同时传进对应的数据，Response.send()为发送一个响应；在设置路由时index和list方法作为回调函数最终执行。</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288; <br></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288; <span style="font-family: 幼圆; font-size: 16px;">流程</span>大概<span style="font-family: 幼圆; font-size: 16px;">了解啦，俺</span>们也就实际搞一把，最easy的一种方式，简单俩步：<br></span></div>
<div><ol>
<li><span style="font-family: 幼圆; font-size: 16px;"><span style="font-family: 幼圆; font-size: 16px;">第一种方式就是在当前的routes/index.js或者routes/test.js中加几行代码如下<br></span></span>
<div class="cnblogs_code">
<pre>exports.test = <span style="color: #0000ff;">function</span><span style="color: #000000;">(req, res){
  res.send('test welcome.');</span><span style="color: #000000;">
};</span></pre>
</div>
<p>&nbsp;</p>
</li>
<li>在app.js文件设置路由那块加上app.get('/test', routes.test);</li>
</ol></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288; 第二种方式就是多了两步，先新建一个模块如test.js文件，输出然后exports对应的方法；在app.js中require这个模块，再加一行设置路由即完成了。<br></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp;</span></div>
<div><strong><span style="font-family: 幼圆; font-size: 18px; background-color: #ccffff;">&#12288;&#12288;快速炫起来，集成Bootstrap：&#12288;&#12288;</span></strong></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;JS工程师使用Nodejs上手还是以快速搭建网站为主，所以才会介绍Express，那么为了让网站更快的体面起来，集成使用Bootstrap就是上佳选择，非常喜欢其响应式布局和整体系的脚手架。</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;PS：因为Bootstrap的JS插件都依赖jQeury，所以jQuery也一并引入了。</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp;</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288; 前文已经说到了，静态文件都放在public文件夹中，切文件夹内已经帮我们把类目都分好了，images、 javascripts、 stylesheets。</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288; 分别引入bootstrap.min.css文件至stylesheets目录下；jquery-1.x.x.min.js和bootstrap.min.js放到javascripts文件夹下。<br></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288; 然后俺们修改view/index.html把文件引入使用即可，下面放出俺在bootstrap demo的基础改的index.html，大家随意拿去使用和修改。<br></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;"><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288;</span></span>
<div onclick="cnblogs_code_show('d4005c23-cd80-44fa-b152-9c3cc32606aa')" class="cnblogs_code"><img alt="" src="http://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif" class="code_img_closed" id="code_img_closed_d4005c23-cd80-44fa-b152-9c3cc32606aa"><img alt="" src="http://images.cnblogs.com/OutliningIndicators/ExpandedBlockStart.gif" onclick="cnblogs_code_hide('d4005c23-cd80-44fa-b152-9c3cc32606aa',event)" style="display: none;" class="code_img_opened" id="code_img_opened_d4005c23-cd80-44fa-b152-9c3cc32606aa">
<div class="cnblogs_code_hide" id="cnblogs_code_open_d4005c23-cd80-44fa-b152-9c3cc32606aa">
<pre>&lt;!DOCTYPE html&gt;
&lt;html lang="zh-cn"&gt;
  &lt;head&gt;
    &lt;title&gt;&lt;%= title %&gt;&lt;/title&gt;
    &lt;meta charset="utf-8"&gt;
    &lt;meta name="viewport" content="width=device-width, initial-scale=1.0"&gt;
    &lt;meta http-equiv="X-UA-Compatible" content="IE=edge"&gt;
    &lt;link href="/stylesheets/bootstrap.min.css" rel="stylesheet"&gt;
    &lt;!--&lt;link href="/stylesheets/base.css" rel="stylesheet"&gt;--&gt;
    &lt;!--&lt;link href="/stylesheets/common.css" rel="stylesheet"&gt;--&gt;
    &lt;!--&lt;link href="/stylesheets/page.css" rel="stylesheet"&gt;--&gt;
    &lt;!-- 建议在项目中把CSS分好level，好维护和管理 --&gt;
    &lt;style&gt;<span style="color: #000000;">
        html, body { overflow</span>-<span style="color: #000000;">x: hidden;}
        body { padding</span>-<span style="color: #000000;">top: 70px;background:#f1f1f1; }
        footer { padding:20px </span>0 10px;text-align:center;font-weight:bold;border-top:1px solid #ddd;margin-<span style="color: #000000;">top:30px;}
        .header</span>-navbar-<span style="color: #000000;">style {
            filter:alpha(opacity</span>=90<span style="color: #000000;">);
            </span>-moz-opacity:0.9<span style="color: #000000;">;
            </span>-khtml-opacity: 0.9<span style="color: #000000;">;
            opacity: </span>0.9<span style="color: #000000;">;
            background: linear</span>-gradient(45deg, rgb(60, 8, 34) 0%, rgb(49, 79, 117) 100%<span style="color: #000000;">);
            border:1px solid #aaa;
            font</span>-<span style="color: #000000;">size:16px;
        }
        .beige {background:beige;}
        .bisque {background:bisque;}
        .darkseagreen{ background:darkseagreen;}
    </span>&lt;/style&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;div class="navbar navbar-fixed-top header-navbar-style navbar-inverse" role="navigation"&gt;
      &lt;div class="container"&gt;
        &lt;div class="navbar-header"&gt;
          &lt;button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-collapse"&gt;
            &lt;span class="sr-only"&gt;Toggle navigation&lt;/span&gt;
            &lt;span class="icon-bar"&gt;&lt;/span&gt;
            &lt;span class="icon-bar"&gt;&lt;/span&gt;
            &lt;span class="icon-bar"&gt;&lt;/span&gt;
          &lt;/button&gt;
          &lt;a class="navbar-brand" href="/"&gt;Product&lt;/a&gt;
        &lt;/div&gt;
        &lt;div class="collapse navbar-collapse"&gt;
          &lt;ul class="nav navbar-nav"&gt;
            &lt;li class="active"&gt;&lt;a href="/"&gt;Home&lt;/a&gt;&lt;/li&gt;
            &lt;li class=""&gt;&lt;a href="/contactus"&gt;Contact&lt;/a&gt;&lt;/li&gt;
            &lt;li class="dropdown"&gt;
              &lt;a href="#" class="dropdown-toggle" data-toggle="dropdown"&gt;Dropdown &lt;b class="caret"&gt;&lt;/b&gt;&lt;/a&gt;
              &lt;ul class="dropdown-menu beige"&gt;
                &lt;li&gt;&lt;a href="#"&gt;Action&lt;/a&gt;&lt;/li&gt;
                &lt;li&gt;&lt;a href="#"&gt;Another action&lt;/a&gt;&lt;/li&gt;
                &lt;li&gt;&lt;a href="#"&gt;Something <span style="color: #0000ff;">else</span> here&lt;/a&gt;&lt;/li&gt;
                &lt;li class="divider"&gt;&lt;/li&gt;
                &lt;li&gt;&lt;a href="#"&gt;Separated link&lt;/a&gt;&lt;/li&gt;
                &lt;li class="divider"&gt;&lt;/li&gt;
                &lt;li&gt;&lt;a href="#"&gt;One more separated link&lt;/a&gt;&lt;/li&gt;
              &lt;/ul&gt;
            &lt;/li&gt;
            &lt;li class=""&gt;&lt;a href="/faq"&gt;FAQ&lt;/a&gt;&lt;/li&gt;
          &lt;/ul&gt;
        &lt;/div&gt;&lt;!-- /.nav-collapse --&gt;
      &lt;/div&gt;&lt;!-- /.container --&gt;
    &lt;/div&gt;&lt;!-- /.navbar --&gt;

    &lt;!-- 以上位置建议创建个header.html维护起来 --&gt;

    &lt;style&gt;<span style="color: #000000;">
      @media screen and (max</span>-<span style="color: #000000;">width: 767px) {
        .row</span>-<span style="color: #000000;">offcanvas { position: relative;
        </span>-webkit-transition: all 0.25s ease-<span style="color: #000000;">out;
        </span>-moz-transition: all 0.25s ease-<span style="color: #000000;">out;
        transition: all </span>0.25s ease-<span style="color: #000000;">out;
      }
      .row</span>-offcanvas-right .sidebar-offcanvas { right: -50%; <span style="color: #008000;">/*</span><span style="color: #008000;"> 6 columns </span><span style="color: #008000;">*/</span><span style="color: #000000;"> }
      .row</span>-offcanvas-left .sidebar-offcanvas { left: -50%; <span style="color: #008000;">/*</span><span style="color: #008000;"> 6 columns </span><span style="color: #008000;">*/</span><span style="color: #000000;"> }
      .row</span>-offcanvas-right.active { right: 50%; <span style="color: #008000;">/*</span><span style="color: #008000;"> 6 columns </span><span style="color: #008000;">*/</span><span style="color: #000000;"> }
      .row</span>-offcanvas-left.active { left: 50%; <span style="color: #008000;">/*</span><span style="color: #008000;"> 6 columns </span><span style="color: #008000;">*/</span><span style="color: #000000;"> }
      .sidebar</span>-offcanvas { position: absolute; top: 0; width: 50%; <span style="color: #008000;">/*</span><span style="color: #008000;"> 6 columns </span><span style="color: #008000;">*/</span><span style="color: #000000;"> } }
    </span>&lt;/style&gt;

    &lt;div class="container"&gt;
      &lt;div class="row row-offcanvas row-offcanvas-right"&gt;
        &lt;div class="col-xs-12 col-sm-9"&gt;
          &lt;p class="pull-right visible-xs"&gt;
            &lt;button type="button" class="btn btn-primary btn-xs" data-toggle="offcanvas"&gt;Toggle nav&lt;/button&gt;
          &lt;/p&gt;
          &lt;div class="jumbotron bisque"&gt;
            &lt;h1&gt;Welcome &lt;%= title %&gt;!&lt;/h1&gt;
            &lt;p&gt;This is an example to show the potential of an offcanvas layout pattern <span style="color: #0000ff;">in</span> Bootstrap. Try some responsive-range viewport sizes to see it <span style="color: #0000ff;">in</span> action.&lt;/p&gt;
          &lt;/div&gt;
          &lt;div class="row"&gt;
            &lt;div class="col-6 col-sm-6 col-lg-4"&gt;
              &lt;h2&gt;Heading&lt;/h2&gt;
              &lt;p&gt;Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus. Etiam porta sem malesuada magna mollis euismod. Donec sed odio dui. &lt;/p&gt;
              &lt;p&gt;&lt;a class="btn btn-default" href="#" role="button"&gt;View details &amp;raquo;&lt;/a&gt;&lt;/p&gt;
            &lt;/div&gt;&lt;!--/span--&gt;
            &lt;div class="col-6 col-sm-6 col-lg-4"&gt;
              &lt;h2&gt;Heading&lt;/h2&gt;
              &lt;p&gt;Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus. Etiam porta sem malesuada magna mollis euismod. Donec sed odio dui. &lt;/p&gt;
              &lt;p&gt;&lt;a class="btn btn-default" href="#" role="button"&gt;View details &amp;raquo;&lt;/a&gt;&lt;/p&gt;
            &lt;/div&gt;&lt;!--/span--&gt;
            &lt;div class="col-6 col-sm-6 col-lg-4"&gt;
              &lt;h2&gt;Heading&lt;/h2&gt;
              &lt;p&gt;Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus. Etiam porta sem malesuada magna mollis euismod. Donec sed odio dui. &lt;/p&gt;
              &lt;p&gt;&lt;a class="btn btn-default" href="#" role="button"&gt;View details &amp;raquo;&lt;/a&gt;&lt;/p&gt;
            &lt;/div&gt;&lt;!--/span--&gt;
            &lt;div class="col-6 col-sm-6 col-lg-4"&gt;
              &lt;h2&gt;Heading&lt;/h2&gt;
              &lt;p&gt;Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus. Etiam porta sem malesuada magna mollis euismod. Donec sed odio dui. &lt;/p&gt;
              &lt;p&gt;&lt;a class="btn btn-default" href="#" role="button"&gt;View details &amp;raquo;&lt;/a&gt;&lt;/p&gt;
            &lt;/div&gt;&lt;!--/span--&gt;
            &lt;div class="col-6 col-sm-6 col-lg-4"&gt;
              &lt;h2&gt;Heading&lt;/h2&gt;
              &lt;p&gt;Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus. Etiam porta sem malesuada magna mollis euismod. Donec sed odio dui. &lt;/p&gt;
              &lt;p&gt;&lt;a class="btn btn-default" href="#" role="button"&gt;View details &amp;raquo;&lt;/a&gt;&lt;/p&gt;
            &lt;/div&gt;&lt;!--/span--&gt;
            &lt;div class="col-6 col-sm-6 col-lg-4"&gt;
              &lt;h2&gt;Heading&lt;/h2&gt;
              &lt;p&gt;Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus. Etiam porta sem malesuada magna mollis euismod. Donec sed odio dui. &lt;/p&gt;
              &lt;p&gt;&lt;a class="btn btn-default" href="#" role="button"&gt;View details &amp;raquo;&lt;/a&gt;&lt;/p&gt;
            &lt;/div&gt;&lt;!--/span--&gt;
          &lt;/div&gt;&lt;!--/row--&gt;
        &lt;/div&gt;&lt;!--/span--&gt;

        &lt;div class="col-xs-6 col-sm-3 sidebar-offcanvas" id="sidebar" role="navigation"&gt;
          &lt;div class="list-group"&gt;
            &lt;a target="_blank" href="#" class="list-group-item"&gt;Link&lt;/a&gt;
            &lt;a href="#" class="list-group-item"&gt;Link&lt;/a&gt;
            &lt;a href="#" class="list-group-item"&gt;Link&lt;/a&gt;
            &lt;a href="#" class="list-group-item"&gt;Link&lt;/a&gt;
            &lt;a href="#" class="list-group-item"&gt;Link&lt;/a&gt;
            &lt;a href="#" class="list-group-item"&gt;Link&lt;/a&gt;
            &lt;a href="#" class="list-group-item"&gt;Link&lt;/a&gt;
            &lt;a href="#" class="list-group-item"&gt;Link&lt;/a&gt;
            &lt;a href="#" class="list-group-item"&gt;Link&lt;/a&gt;
            &lt;a href="#" class="list-group-item"&gt;Link&lt;/a&gt;
          &lt;/div&gt;
        &lt;/div&gt;&lt;!--/span--&gt;
      &lt;/div&gt;&lt;!--/row--&gt;
    &lt;/div&gt;&lt;!--/.container--&gt;

    &lt;!-- 从header.html之后到此可分为page层 --&gt;

    &lt;footer class="darkseagreen"&gt;
        &lt;p&gt;Copyright &amp;copy; 2014. Designed by nieweidong.&lt;/p&gt;
    &lt;/footer&gt;
    &lt;script src="/javascripts/jquery-1.11.0.min.js"&gt;&lt;/script&gt;
    &lt;script src="/javascripts/bootstrap.min.js"&gt;&lt;/script&gt;
    &lt;script&gt;<span style="color: #000000;">
      $(document).ready(</span><span style="color: #0000ff;">function</span><span style="color: #000000;">() {
        $(</span>'[data-toggle=offcanvas]').click(<span style="color: #0000ff;">function</span><span style="color: #000000;">() {
          $(</span>'.row-offcanvas').toggleClass('active'<span style="color: #000000;">);
        });
      });
    </span>&lt;/script&gt;
  &lt;/body&gt;
&lt;/html&gt;</pre>
</div>
<span class="cnblogs_code_collapse">View Code </span></div>
<p>&#12288;&#12288; 如果样式有问题请检查下bootstrap的路径是否正确引入。</p>
<p>&#12288;&#12288; 启动项目之后觉得 高大上 很简单，有木有！！</p>
</div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288; <br></span></div>
<div><span style="background-color: #ccffff;"><strong><span style="font-family: 幼圆; font-size: 18px;">&#12288;&#12288;FAQ&amp;总结：&#12288;&#12288;</span></strong></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp;&nbsp; 俺们的express项目暂时，且express也并没有涉及到任何数据库，这个事情需要第三方node模块，比如mysql或者MongoDB，后续俺会有一章单独介绍这块。</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288; express也不是Node中web框架的唯一选择，不过由于其文档较全，所以才以其为示例为大家介绍，其原理和实现其实细化之后并不复杂，也希望更多的JS工程师折腾出自己的Web框架。<br></span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&nbsp; &nbsp; &nbsp;</span></div>
<div><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288; 尼玛还有几个小时就到3月了，一月一篇可是俺的目标，所以全面的demo俺之后再补上哈。<br></span></div>
<div>&nbsp;</div>
<div>&nbsp;</div>
<div>
<div style="color: #000000; font-family: 微软雅黑; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: normal; orphans: 2; text-align: -webkit-auto; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px; font-size: medium;"><span style="font-size: 18px;"><strong><span style="font-family: 幼圆; background-color: #ccffff;">&#12288;&#12288;参考资料：&#12288;&#12288;</span></strong></span></div>
<div style="color: #000000; font-family: 微软雅黑; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: normal; orphans: 2; text-align: -webkit-auto; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px; font-size: medium;"><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288;<a target="_blank" href="http://express.jsbin.cn/api.html">http://express.jsbin.cn/api.html</a></span></div>
<div style="color: #000000; font-family: 微软雅黑; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: normal; orphans: 2; text-align: -webkit-auto; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px; font-size: medium;"><span style="font-family: 幼圆; font-size: 16px;">&#12288;&#12288;<a target="_blank" href="http://www.embeddedjs.com">http://www.embeddedjs.com</a></span></div>
<div style="color: #000000; font-family: 微软雅黑; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: normal; orphans: 2; text-align: -webkit-auto; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px; font-size: medium;">&nbsp;</div>
<div style="color: #000000; font-family: 微软雅黑; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: normal; orphans: 2; text-align: -webkit-auto; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px; font-size: medium;">&nbsp;</div>
</div>
</div>
<div><span style="font-family: 幼圆; font-size: 16px; background-color: #ccffff;">&#12288;&#12288;<span style="font-size: 18px;"><strong>Node的小基友supervisor 和 forever 不要忘记了，相信你会喜欢他们的:)&#12288;&#12288;</strong></span></span></div></div>
