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

<div id="cnblogs_post_body"><p>&#12288;&#12288;从事web开发也有些日子了，cookie 是个啥差不多能说明白，可是实际自己一上手操作就是得去搜索(你们懂的)，结果被鄙视了...所以就写一篇博文做为自己的学习笔记，嘿嘿，博客的好处在此体现出来了。</p>
<p>&nbsp;</p>
<p><span style="font-size: 18pt;"><strong><span style="background-color: #ccffff;">&#12288;&#12288;什么是 Cookie</span></strong></span></p>
<p>&#12288;&#12288;“cookie 是存储于访问者的计算机中的变量。每当同一台计算机通过浏览器请求某个页面时，就会发送这个 cookie。你可以使用 JavaScript 来创建和取回 cookie 的值。” -&nbsp;w3school<br>&#12288;&#12288;cookie 是访问过的网站创建的文件，用于存储浏览信息，例如个人资料信息。</p>
<p>&#12288;&#12288;从JavaScript的角度看，cookie 就是一些字符串信息。这些信息存放在客户端的计算机中，用于客户端计算机与服务器之间传递信息。</p>
<p>&#12288;&#12288;在JavaScript中可以通过 document.cookie 来读取或设置这些信息。由于 cookie 多用在客户端和服务端之间进行通信，所以除了JavaScript以外，服务端的语言（如PHP）也可以存取 cookie。</p>
<p>&nbsp;</p>
<p><span style="font-size: 18pt;"><strong><span style="background-color: #ccffff;">&#12288;&#12288;Cookie 基础知识</span></strong></span></p>
<ul>
<li>cookie 是有大小限制的，每个 cookie 所存放的数据不能超过4kb，如果 cookie 字符串的长度超过4kb，则该属性将返回空字符串。</li>
<li>由于 cookie 最终都是以文件形式存放在客户端计算机中，所以查看和修改 cookie 都是很方便的，这就是为什么常说 cookie 不能存放重要信息的原因。</li>
<li>每个 cookie 的格式都是这样的：&lt;cookie名&gt;=&lt;值&gt;；名称和值都必须是合法的标示符。</li>
<li>cookie 是存在 有效期的。在默认情况下，一个 cookie 的生命周期就是在浏览器关闭的时候结束。如果想要 cookie 能在浏览器关掉之后还可以使用，就必须要为该 cookie 设置有效期，也就是 cookie 的失效日期。</li>
<li>alert(typeof document.cookie)&#12288;&#12288;结果是&nbsp;string，曾经我以为是array，还闹过笑话...囧</li>
<li>cookie 有<strong>域和路径</strong>这个概念。域就是domain的概念，因为浏览器是个注意安全的环境，所以不同的域之间是不能互相访问 cookie 的(当然可以通过特殊设置的达到 cookie 跨域访问)。路径就是routing的概念，一个网页所创建的 cookie 只能被与这个网页在同一目录或子目录下得所有网页访问，而不能被其他目录下得网页访问（这句话有点绕，一会看个例子就好理解了）。</li>
<li>其实创建cookie的方式和定义变量的方式有些相似，都需要使用 cookie 名称和 cookie 值。同个网站可以创建多个 cookie ，而多个 cookie 可以存放在同一个cookie 文件中。</li>
</ul>
<div>&nbsp;</div>
<div><span style="font-size: 18pt;"><strong><span style="background-color: #ccffff;">&#12288;&#12288;Cookie常见问题</span></strong></span></div>
<div>
<ul>
<li>cookie 存在两种类型：
<ul>
<li>你浏览的当前网站本身设置的 cookie</li>
<li>来自在网页上嵌入广告或图片等其他域来源的&nbsp;第三方 cookie (网站可通过使用这些 cookie 跟踪你的使用信息)</li>
</ul>
</li>
</ul>
<ul>
<li>刚刚基础知识里面有说到 cookie 生命周期的问题，其实 cookie 大致可分为两种状态：
<ul>
<li>临时性质的cookie。当前使用的过程中网站会储存一些你的个人信息，当浏览器关闭后这些信息也会从计算机中删除</li>
<li>设置失效时间的cookie。就算浏览器关闭了，这些信息业依然会在计算机中。如&nbsp;登录名称和密码，这样无须在每次到特定站点时都进行登录。这种cookie 可在计算机中保留几天、几个月甚至几年</li>
</ul>
</li>
<li>cookie 有两种清除方式：
<ul>
<li>通过浏览器工具清除 cookie (有第三方的工具，浏览器自身也有这种功能)</li>
<li>通过设置 cookie 的有效期来清除 cookie</li>
<li>注：删除 cookie 有时可能导致某些网页无法正常运行</li>
</ul>
</li>
<li>浏览器可以通过设置来接受和拒绝访问 cookie。</li>
<li>出于功能和性能的原因考虑，建议尽量降低 cookie 的使用数量，并且要尽量使用小 cookie。</li>
<li>关于cookie编码的细节问题将会在cookie高级篇中单独介绍。</li>
<li>假如是本地磁盘中的页面，chrome的控制台是无法用JavaScript读写操作 cookie 的，解决办法...换一个浏览器^_^。</li>
</ul>
</div>
<div>&nbsp;</div>
<p><span style="font-size: 18pt;"><strong><span style="background-color: #ccffff;">&#12288;&#12288;Cookie基础用法</span></strong></span></p>
<p><span style="font-size: 16px;"><strong>&#12288;&#12288;一.简单的存取操作</strong></span></p>
<p>&#12288;&#12288;在使用JavaScript存取 cookie 时，必须要使用Document对象的 cookie 属性；一行代码介绍如何创建和修改一个 cookie ：</p>
<div class="cnblogs_code">
<pre>&#12288;&#12288;document.cookie  = <span style="color: #800000;">'</span><span style="color: #800000;">username=Darren</span><span style="color: #800000;">'</span></pre>
</div>
<p>&#12288;&#12288;以上代码中'username'表示 cookie 名称，'Darren'表示这个名称对应的值。假设 cookie 名称并不存在，那么就是创建一个新的 cookie；如果存在就是修改了这个 cookie 名称对应的值。如果要多次创建 cookie ，重复使用这个方法即可。</p>
<p>&nbsp;</p>
<p>&#12288;<strong><span style="font-size: 16px;">&#12288;二.cookie的读取操作</span></strong></p>
<p>&#12288;&#12288;要精确的对 cookie 进行读取其实很简单，就是对字符串进行操作。从w3school上copy这段代码来做分析：</p>
<div class="cnblogs_code">
<pre><span style="color: #0000ff;">function</span> getCookie(c_name){<br>&#12288;&#12288;&#12288;&#12288;<span style="color: #0000ff;">if</span> (document.cookie.length&gt;0){&#12288;&#12288;<span style="color: #008000;">//</span><span style="color: #008000;">先查询cookie是否为空，为空就return ""</span><span style="color: #008000;"><br></span>&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;c_start=document.cookie.indexOf(c_name + "=")&#12288;&#12288;<span style="color: #008000;">//通过String对象的indexOf()来检查这个cookie是否存在，不存在就为 -1</span><span style="color: #008000;">&#12288;&#12288;</span><span style="color: #008000;"><br></span>&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;<span style="color: #0000ff;">if</span> (c_start!=-1){ <br>&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;c_start=c_start + c_name.length+1&#12288;&#12288;<span style="color: #008000;">//最后这个+1其实就是表示"="号啦，这样就获取到了cookie值的开始位置<br></span>&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;c_end=document.cookie.indexOf(";",c_start)&#12288;&#12288;<span style="color: #008000;">//其实我刚看见indexOf()第二个参数的时候猛然有点晕，后来想起来表示指定的开始索引的位置...这句是为了得到值的结束位置。因为需要考虑是否是最后一项，所以通过";"号是否存在来判断<br></span>&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;<span style="color: #0000ff;">if</span> (c_end==-1) c_end=document.cookie.length&#12288;&#12288;<span style="color: #008000;"><br></span>&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;<span style="color: #0000ff;">return</span> unescape(document.cookie.substring(c_start,c_end))&#12288;&#12288;<span style="color: #008000;">//通过substring()得到了值。想了解unescape()得先知道escape()是做什么的，都是很重要的基础，想了解的可以搜索下，在文章结尾处也会进行讲解cookie编码细节<br></span>&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;} <br>&#12288;&#12288;&#12288;&#12288;}<br>&#12288;&#12288;&#12288;&#12288;<span style="color: #0000ff;">return</span> ""<br>&#12288;&#12288;}&#12288;&#12288;</pre>
</div>
<p>&#12288;&#12288;当然想实现读取cookie的方法还有不少，比如数组，正则等，这里就不往细说了。</p>
<p>&nbsp;</p>
<p><span style="font-size: 16px;"><strong>&#12288;&#12288;三.设置cookie的有效期</strong></span></p>
<p>&#12288;&#12288;文章中常常出现的 cookie 的生命周期也就是有效期和失效期，即 cookie 的存在时间。在默认的情况下，cookie 会在浏览器关闭的时候自动清除，但是我们可以通过expires来设置 cookie 的有效期。语法如下：</p>
<div class="cnblogs_code">
<pre>&#12288;&#12288;document.cookie = "name=value;expires=date"</pre>
</div>
<p>&#12288;&#12288;上面代码中的date值为GMT(<span class="web-item">格林威治时间)</span>格式的日期型字符串，生成方式如下：</p>
<div class="cnblogs_code">
<pre><span style="color: #0000ff;">&#12288;&#12288;var</span> _date = <span style="color: #0000ff;">new</span> Date();<br><span style="color: #0000ff;">&#12288;&#12288;</span>_date.setDate(_date.getDate()+30);<br>&#12288;&#12288;_date.toGMTString();</pre>
</div>
<p>&#12288;&#12288;上面三行代码分解为几步来看：</p>
<ul>
<li>通过new生成一个Date的实例，得到当前的时间；</li>
<li>getDate()方法得到当前本地月份中的某一天，接着加上30就是我希望这个cookie能过在本地保存30天；</li>
<li>接着通过setDate()方法来设置时间；</li>
<li>最后 用toGMTString()方法把Date对象转换为字符串，并返回结果</li>
</ul>
<p>&#12288;&#12288;通过下面这个完整的函数来说明在创建 cookie 的过程中我们需要注意的地方 - 从w3school复制下来的。创建一个在 cookie 中存储信息的函数：</p>
<div class="cnblogs_code">
<pre><span style="color: #008080;">1</span> &#12288;<span style="color: #0000ff;">function</span> setCookie(c_name, value, expiredays){<br><span style="color: #008080;">2</span> &#12288;&#12288;&#12288;&#12288;<span style="color: #0000ff;">var</span> exdate=<span style="color: #0000ff;">new</span> Date();<br><span style="color: #008080;">3</span> &#12288;&#12288;&#12288;&#12288;exdate.setDate(exdate.getDate() + expiredays);<br><span style="color: #008080;">4</span> &#12288;&#12288;&#12288;&#12288;document.cookie=c_name+ "=" + escape(value) + ((expiredays==<span style="color: #0000ff;">null</span>) ? "" : ";expires="+exdate.toGMTString());<br><span style="color: #008080;">5</span> &#12288;&#12288;}<br><span style="color: #008080;">6</span> &#12288;&#12288;使用方法：setCookie('username','Darren',30)  </pre>
</div>
<p>&#12288;&#12288;现在我们这个函数是按照天数来设置cookie的有效时间，如果想以其他单位（如：小时）来设置，那么改变第三行代码即可：</p>
<div class="cnblogs_code">
<pre>&#12288;&#12288;exdate.setHours(exdate.getHours() + expiredays);</pre>
</div>
<p>&#12288;&#12288;这样设置以后的cookie有效期就是按照小时为单位的。</p>
<p>&#12288;&#12288;常见问题中有提到清除&nbsp;cookie 的两种方法，现在要说的是使 cookie 失效，通过把有效期的时间设置为一个已过期的时间。既然已经有了设置有效期的方法，那么设置失效期的方法就请感兴趣的朋友自己动手了^_^。下面继续比较深的cookie话题。</p>
<p>&nbsp;</p>
<p><span style="background-color: #ccffff; font-size: 18pt;"><strong>&#12288;&#12288;Cookie 高级篇<br></strong></span></p>
<p><span style="font-size: 16px;"><strong>&#12288;&#12288;一.cookie 路径概念</strong></span></p>
<p>&#12288;&#12288;在基础知识中有提到 cookie 有域和路径的概念，现在来介绍路径在 cookie 中的作用。</p>
<p>&#12288;&#12288;cookie 一般都是由于用户访问页面而被创建的，可是并不是只有在创建 cookie 的页面才可以访问这个 cookie。</p>
<p>&#12288;&#12288;默认情况下，只有与创建 cookie 的页面在同一个目录或子目录下的网页才可以访问，这个是因为安全方面的考虑，造成不是所有页面都可以随意访问其他页面创建的 cookie。举个例子：</p>
<p>&#12288;&#12288;在 "http://www.cnblogs.com/Darren_code/" 这个页面创建一个cookie，那么在"/Darren_code/"这个路径下的页面如： "http://www.cnblogs.com/Darren_code/archive/2011/11/07/Cookie.html"这个页面默认就能取到cookie信息。</p>
<p>&#12288;&#12288;可在默认情况下， "http://www.cnblogs.com"或者 "http://www.cnblogs.com/xxxx/" 就不可以访问这个 cookie（光看没用，实践出真理^_^）。</p>
<p>&#12288;&#12288;那么如何让这个 cookie 能被其他目录或者父级的目录访问类，通过设置 cookie 的路径就可以实现。例子如下：</p>
<div class="cnblogs_code">
<pre>&#12288;&#12288;document.cookie = "name=value;path=<span style="color: #ff0000;">path</span>"<br>&#12288;&#12288;document.cookie = "name=value;expires=date;path=<span style="color: #ff0000;">path</span>"</pre>
</div>
<p>&nbsp;&#12288;&#12288;红色字体path就是 cookie 的路径，最常用的例子就是让 cookie 在跟目录下,这样不管是哪个子页面创建的 cookie，所有的页面都可以访问到了:</p>
<div class="cnblogs_code">
<pre>&#12288;&#12288;document.cookie = "name=Darren;<span style="color: #ff0000;">path=/</span>"</pre>
</div>
<p>&#12288;&#12288;&nbsp;</p>
<p><span style="font-size: 16px;"><strong>&#12288;&#12288;二.cookie 域概念</strong></span></p>
<p>&#12288;&#12288;路径能解决在同一个域下访问 cookie 的问题，咱们接着说 cookie 实现<strong>同域</strong>之间访问的问题。语法如下：</p>
<div class="cnblogs_code">
<pre>&#12288;&#12288;document.cookie = "name=value;path=path;domain=<span style="color: #ff0000;">domain</span>"</pre>
</div>
<p>&#12288;&#12288;红色的domain就是设置的 cookie 域的值。</p>
<p>&#12288;&#12288;例如&nbsp;"www.qq.com" 与 "sports.qq.com" 公用一个关联的域名"qq.com"，我们如果想让 "sports.qq.com" 下的cookie被&nbsp;"www.qq.com" 访问，我们就需要用到 cookie 的domain属性，并且需要把path属性设置为 "/"。例：</p>
<div class="cnblogs_code">
<pre>&#12288;&#12288;document.cookie = "username=Darren;path=/;domain=<span style="color: #ff0000;">qq.com</span>"</pre>
</div>
<p>&#12288;&#12288;注：一定的是同域之间的访问，不能把domain的值设置成非主域的域名。</p>
<p>&nbsp;</p>
<p><strong><span style="font-size: 16px;">&#12288;&#12288;三.cookie 安全性</span></strong></p>
<p>&#12288;&#12288;通常 cookie 信息都是使用HTTP连接传递数据，这种传递方式很容易被查看，所以 cookie 存储的信息容易被窃取。假如 cookie 中所传递的内容比较重要，那么就要求使用加密的数据传输。</p>
<p>&#12288;&#12288;所以 cookie 的这个属性的名称是“secure”，默认的值为空。如果一个 cookie 的属性为secure，那么它与服务器之间就通过HTTPS或者其它安全协议传递数据。语法如下：</p>
<div class="cnblogs_code">
<pre>&#12288;&#12288;document.cookie = "username=Darren;secure"</pre>
</div>
<p>&#12288;&#12288;把cookie设置为secure，只保证 cookie 与服务器之间的数据传输过程加密，而保存在本地的 cookie文件并不加密。如果想让本地cookie也加密，得自己加密数据。</p>
<p>&#12288;&#12288;注：就算设置了secure 属性也并不代表他人不能看到你机器本地保存的 cookie 信息，所以说到底，别把重要信息放cookie就对了，囧...</p>
<p>&#12288;&#12288;&nbsp;</p>
<p><span style="font-size: 16px;"><strong>&#12288;&#12288;四.cookie 编码细节</strong></span></p>
<p>&#12288;&#12288;原本来想在常见问题那段介绍cookie编码的知识，因为如果对这个不了解的话编码问题确实是一个坑，所以还是详细说说。</p>
<p>&#12288;&#12288;在输入cookie信息时不能包含空格，分号，逗号等特殊符号，而在一般情况下，cookie 信息的存储都是采用未编码的方式。所以，在设置 cookie 信息以前要先使用escape()函数将 cookie 值信息进行编码，在获取到 cookie 值得时候再使用unescape()函数把值进行转换回来。如设置cookie时：</p>
<div class="cnblogs_code">
<pre>&#12288;&#12288;document.cookie = name + "="+ escape (value)</pre>
</div>
<p>&#12288;&#12288;再看看基础用法时提到过的getCookie()内的一句：</p>
<div class="cnblogs_code">
<pre><span style="color: #0000ff;">&#12288;&#12288;return</span> unescape(document.cookie.substring(c_start,c_end))</pre>
</div>
<p>&#12288;&#12288;这样就不用担心因为在cookie值中出现了特殊符号而导致 cookie 信息出错了。</p>
<p>&nbsp;</p>
<p><strong><span style="background-color: #ccffff; font-size: 18pt;">&#12288;&#12288;总结</span></strong></p>
<p>&#12288;&#12288;在工作中越来越感觉到基础的重要性了，有很多技术细节都是要懂不懂或者的懂的不多。为了改善这种情况，打算以后会对知识的细节从点到面的去理解，然后再写博客加深印象，也能分享给更多有需要的朋友。</p>
<p>&#12288;&#12288;今天是感恩节，感谢所有人...</p>
<p>&nbsp;</p>
</div>
