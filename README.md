易信公众平台改版之字体图标
---
> 时隔一又四分之一年，迎来了易信公众平台的改版。作为该项目的元老级开发（自项目成立之初，就参与前端开发工作），虽不能说对整个产品了如指掌，至少在整体的业务需求和功能逻辑方面还是相当清楚的。自去年8月上线以来，到如今，公众平台已迭代了至少20个版本，项目日益庞大，各种历史遗留的坑也越来越难以填补。值此改版之际，一方面解决一些遗留问题，并将有问题的模块控件进行一次重构、优化，另一方面也尝试一些新的东西，比如本文要讲的这个字体图标。

Google一把 `字体图标`，你会发现这早已不是什么新的技术或新的概念，而且很多网站提供了字体图标库的下载（如[Font Awesome](http://www.bootcss.com/p/font-awesome/)、[icomoon](https://icomoon.io/app/#/select)），不会设计的前端ers直接download一份，也很够你的项目用了。另外，国内的很多互联网公司也都产出了自家的字体图标库，比如阿里的[iconfont](http://www.iconfont.cn/repositories/10)（稍安勿躁，我们大网易的字体图标库也已提上日程，相信不久之后就有一套网易风格的图标库了）。

## Get your font icons


如果你不会PS，不会用钢笔工具画图标，只是一只纯粹的前端狗，也没有关系，愉快得从在线网站上下载你需要的图标吧。

**Step1.** 访问 [icomoonAPP](https://icomoon.io/app/#/select)
<pre>icomoon的字体图标应用，支持用户免费添加或购买字体图标库，并生成字体图标文件供下载</pre>
**Step2.** [Add Icons From Library](https://icomoon.io/app/#/select/library)

    用户可以新建自己的工程，从图标库里添加所需的图标到该工程。
	如果你是豪，你也可以购买你需要的图标库。
	icomoon还支持在线简单的编辑每个图标，包括翻转、位置等。 
 
**Step3.** Choose & Download

	筛选你需要的图标（不建议把库里所有的图标都下载，因为很多图标你都不会用到，不要让字体文件拖累你的带宽）
	在Generate Font页你可以进一步编辑图标，修改图标名称或字符，如无需编辑，直接click download按钮吧

## Use font icons in your project

已经准备好了材料，可以在你的项目中大刀霍斧的开用了。先来瞅瞅下载下来的文件：

![](https://raw.githubusercontent.com/lzf0402/blogs/master/imgs/show1.png)

demo.html可以预览你下载下来的字体图标。有了这个demo，前端同学们一眼就知道如何使用了。

展示下易信公众平台的字体图标实践情况：

1.文件目录如下：

![](https://raw.githubusercontent.com/lzf0402/blogs/master/imgs/show2.png)

> 易信公众平台是[MCSS预处理器](https://github.com/leeluolee/mcss)的忠实实践粉，项目的字体文件目录（fonts目录）与mcss目录和生成的css目录处于同一级。其中fticon.mcss下定义了本项目要用的字体图标。

2.fticon.mcss样式片段如下：

	@font-face { 
		font-family: "icomoon";
		src:url("../fonts/icomoon.eot?v=1.5.2"); /* IE9 Compat Modes */
		src:url("../fonts/icomoon.eot?v=1.5.2#iefix") format("embedded-opentype"),/* IE6-IE8 */
			url("../fonts/icomoon.woff?v=1.5.2") format("woff"),  /* Modern Browsers */
			url("../fonts/icomoon.ttf?v=1.5.2") format("truetype"), /* Safari, Android, iOS */
			url("../fonts/icomoon.svg?v=1.5.2#Ionicons") format("svg");  /* Legacy iOS */
		font-weight:normal; font-style:normal;
	}
	
	/* 字体图标基类 */
	.u-ticon{
	    display:inline-block();
	    font-family:'icomoon';
		speak: none; line-height: 1;
		font-style:normal; font-weight:normal; font-variant:normal;
		text-transform:none; text-rendering:auto; 
		-webkit-font-smoothing:antialiased; 
		-moz-osx-font-smoothing:grayscale;
	}
	/* 用户图标 */
	.icon-user:before {
		content: "\e60d";
	}
	...

- **font-face规则**：@font-face能够加载服务器端的字体文件，让客户端显示客户端所没有安装的字体，也就是自定义网页字体，这是CSS3里的新内容（作为前端狗，如果还不知道这条rule，赶紧[猛戳恶补](http://devdocs.io/css/@font-face)下）。`font-family`属性设置文本的字体名称。 `src`属性设置自定义字体的路径,且可以通过`format`设置自定义字体的格式，助于浏览器识别，其值主要有以下几种类型：`truetype`, `opentype`, `truetype-aat`, `embedded-opentype`, `svg`等。icomoon生成的字体文件包含了.eof、.woff、.ttf、.svg格式，基本上能被绝大多数浏览器识别。

- **font-smoothing属性**：设置文本的平滑属性；属性值有：none（不平滑，适用于小像素文本）、subpixel-antialiased（亚像素平滑）、antialiased(灰阶平滑)；经测试，此三值未观察到异样的表现（也可能是我度数太深，看不粗来）。

- **before伪元素**： 通过`content`设置了文本内容。只是IE7及以下不支持该伪元素，所以以上的字体图标在IE7-下也不可见。当然现在越来越多的项目已开始抛弃IE6\7（此2款浏览器滚出前端圈，指日可待），如果你的项目只需支持到IE8+，那么很幸运，你的字体图标就可以采用这种方式来指定啦。
	
关于使用，很简单，在你的标签上设置以上两个类就可以啦~如下：

    <i class="u-fticon icon-user" title="账户设置"></i>

## Demos

下面以公众平台的一按钮切换的实例，来展示使用字体图标的好用。
按钮效果图如下：

![](https://raw.githubusercontent.com/lzf0402/blogs/master/imgs/show3.png)

交互行为就是用户点击按钮会有一个启用状态的切换，而所用的字体图标如下：

![](https://raw.githubusercontent.com/lzf0402/blogs/master/imgs/show4.png)

下面的代码展示只使用一个标签以及JS控制样式切换来实现这一交互。

	/* 切换按钮 */
	.icon-toggle:before {
		content: "\e634";
	}
	/* 按钮-启用停用切换 */
	.u-togbtn{
		$inline-block();position: relative; padding:0 10px 0 60px; 
		height:33px;line-height:33px;font-size: 12px;
		border-radius:3px;text-decoration:none;border-top:1px solid #27add6;
		cursor:pointer;background:#2bbce8;
		&,&:hover{color:#fff;}
		/* 定位字体图标的位置 */
		&.icon-toggle:before{position: absolute;left: 10px;font-size:20px;}
		/* 切换样式，重置了节点的背景色及padding，以及字体图标的颜色和位置 */
		&.z-toggle{
			padding:0 60px 0 10px;background:#f2f4f5;border-top-color: #dfe1e2;
			&,&:hover{color:#666;}
			&.icon-toggle:before{color:#2bbce8;left: auto;right: 10px;}
		}
	}

节点运用样式：

	<b title="点击切换" id="togglebtn" class="u-togbtn icon-toggle">已启用</b>　
	<b title="点击切换" id="togglebtn" class="u-togbtn icon-toggle z-toggle">已停用</b>
按钮的click事件里toggle下`z-toggle`类，即可实现两种状态的切换，`z-toggle`选择器里重置节点以及字体图标的UI。如此，仅使用一个节点，结合样式切换，就可实现按钮切换的效果。当然，通过传统的切图也是可以轻松实现这一效果，但在可维护方面，字体图标还是远胜一筹。试想下，如果想改一下配色方案，你无需重新切图，只要修改样式里的颜色值就可以啦~~

## Why use it？

使用字体图标，最开心的，我想肯定是我们前端ers。

首先，你可以愉快的跟PS这个`打开要半天的耗内存大户`say Bye啦。不需要切图、不用sprite，也不用辛苦的去调你的`background-position`值啦。

再者，方便维护。如果要修改配色或者换图标，都是分分钟搞定，不再牵涉图片操作，只要修改css文件即可。

最后，

当然，我们的设计师也是一大受益群体。很多常规的图标不再需要设计，可以直接拿来使用，如果形成一个图标库，以后直接从库里找就可以了。
 
## The End
字体图标已不仅仅是前端skill，许多喜欢拥抱扁平化的设计师也越来越爱用。






