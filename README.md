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
	在Generate Font页你可以进一步编辑图标，修改图标名称或字符，如果无需编辑，直接click download按钮下载吧

## Use font icons in your project

已经准备好了材料，可以在你的项目中大刀霍斧的开用了。先来瞧瞧下载下来的文件：


More info: [Server](http://hexo.io/docs/server.html)

## Demos

``` bash
$ hexo generate
```

More info: [Generating](http://hexo.io/docs/generating.html)

## Why use it？

``` bash
$ hexo deploy
```
 
## The End
字体图标已不仅仅是前端skill，许多喜欢拥抱扁平化的设计师也越来越爱用。