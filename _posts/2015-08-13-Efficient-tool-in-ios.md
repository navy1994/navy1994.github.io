---
layout: post
title:  提高iOS开发效率的方法和工具 
date:   2015-8-13 13:22:11
category: "iOS"
---



 介绍

这篇文章主要是介绍一下我在iOS开发中使用到的一些可以提升开发效率的方法和工具。

IDE

首先要说的肯定是IDE了，说到IDE，Xcode不能跑，当然你也可能同时在使用AppCode等其他的IDE，在这里我主要介绍Xcode中提升开发效率的方法。

1.善用快捷键

快捷键是开发中必不可少的，当你善于使用快捷键的时候，十指在键盘上飞舞，那画面太美，我不敢想象。
  
    [常用快捷键操作](http://www.cocoachina.com/ios/20141224/10752.html)

2.常用代码片段

开发中有一些常用的代码，可以放到代码片段中，然后下次你就可以使用快捷方法来使用这些代码了，给大家看下我的Xcode中部分代码片段:


   
    [偷懒小技巧](http://www.2cto.com/kf/201409/336245.html)

3.Xcode插件

我想插件是Xcode必不可少的把
   
    [那些不能错过的Xcode插件](http://www.cocoachina.com/industry/20130918/7022.html)

除此之外，我自己还经常用到的插件有：

1.[快速Add #import](https://github.com/markohlebar/Peckham)

2.[查看项目的’TODO’,’FIXME’等](https://github.com/trawor/XToDo)

在此强烈推荐给大家。

你可能想，如果没有我要用的插件怎么办？少年，这个时候就要自己动手丰衣足食了,我想你可以看看这个Xcode6插件开发入门。

4.注释

注释的作用就不多说了，而且现在公司都要求代码必须有注释。

之前一直在用 [喵神onevcat](http://weibo.com/onevcat?from=myfollow_all) 开源的 [VVDocumenter-Xcode](https://github.com/onevcat/VVDocumenter-Xcode).

但是后来觉得这种注释会有这样一个问题：一个注释多三行

	

/**

 *  顶部公告btn

 */

@property (nonatomic, strong) UIButton *topAnnouncementBtn;

接口用这种方法会简单明了，但是属性的话，总感觉.h文件好多东西（其实没几个属性啊??????）

后来换成这样：



/**顶部公告btn */

@property (nonatomic, strong) UIButton *topAnnouncementBtn;

还是多一行，再后来换成这样：


	

@property (nonatomic, strong) UIButton *topAnnouncementBtn; // 顶部公告btn

但是这种方式，在你使用这个属性的时候，是不会有注释提示的。没有就没有把，遇见不明大意的属性，到时候再跳到.h 文件 看一眼。(“呸，你怎么这么容易就妥协了！！！”，我当时应该在心里暗暗骂自己的）

之后某天在微博上看到 [芳仔小脚印](http://weibo.com/JoanfenZhang) 的博客 [我是如何收拾代码的](http://my.oschina.net/joanfen/blog/415058) 中介绍她是这样注释属性的：


	

UIButton *btnSend;/**< 发送按钮 */


试用了一下，很方便。之后一直用这种方法做属性注释，在这里分享给大家。

感谢 芳仔小脚印 的分享。

网络数据相关

1.调试接口

少年，你还在写方法调试接口吗？如果是，那你一定需要下面这2个了哈:



[DHC](http://chrome-extension//aejoelaoggembcahagimdiliamlcdmfm/dhc.html) 在线调试接口，支持HTTP和HTTPS呦。


[Postman](http://chromecj.com/web-development/2014-09/60.html) 一款功能强大的网页调试与发送网页HTTP请求的Chrome插件。(感谢[叶孤城___](http://weibo.com/u/1438670852?from=feed&loc=nickname)提醒)

2.JSON数据编辑

废话不多说，直接上图：


    [JSON Editor Online](http://chrome-extension//lhkmoheomjbkfloacpgllgjcamhihfaj/index.html)


[JSON格式化工具](http://www.runoob.com/tool/json/index.html) (感谢[iOS程序犭袁](http://weibo.com/luohanchenyilong?from=feed&loc=nickname) 提供)

UI相关

1.距离

不行！说的是20px！差1px，2px，5px，10px，都不算20px！

遇到有像素眼的设计师，想哭的心情总是有。但是他们可能有时候会忘记标X、Y，或者就是宽高，下面是我司UI给的一张图：



魂淡，说好的X，Y呢？

然后我最开始是这样做的



可是总会有辣么一点误差，而且费眼。。。后来我偶然听一个产品朋友说他们在用[马克鳗](http://www.getmarkman.com/)标图，它有免费和收费2个版本，免费版本可以使用基本功能，感觉还不错。

今天喵神[onevcat](http://weibo.com/onevcat?from=myfollow_all)在微博发了一个测量的工具：[Pixel Winch](http://www.ricciadams.com/projects/pixel-winch) ,试了一下，比[马克鳗](http://www.getmarkman.com/)好使。

2.图片压缩

我们UI就不太注重图片的大小，尼玛，有一次给的图片有4M多，害我自己还得压缩一遍

[tinypng](https://tinypng.com/)，保质压缩，我感觉还不错，推荐给我们UI和后台，他们用过之后都说好

[tinypng批量压缩图片脚本](https://github.com/ylovern/GGTinypng) 配套使用更佳。(感谢[newbee_nAn](http://weibo.com/gunnergao) 提供)

3.AppIcon

AppIcon只需要UI提供一张1024*1024的图就可以了，具体的icon可以用[Prepo](https://itunes.apple.com/tw/app/prepo/id476533227?mt=12)生成



两地办公

假设这么一种情况：公司用的是SVN，公司一台公司电脑，家里一台自己电脑，有时候可能想回来后接着敲代码，怎么办？

再假设这么一种情况：公司用的是SVN，产品想实现一种效果，但是你又不确定能不能写出来，所以你可能会纠结要不要在公司项目上改动，怎么办？

如果有上述两种烦恼，那么Github 和 Bitbucket 是您的首选，具体选哪个，这里有一篇对比文章:[GitHub vs. Bitbucket 不只是功能不同](http://www.oschina.net/translate/bitbucket-vs-github-its-more-than-just-features).

Github

Github上好的开源项目太多，一个一个的star，太慢了，怎么破？

1
	

language:Objective-C stars:>900


这个其实就是Github的Advanced search功能：



小伙伴们切记啊，star后并不代表你就掌握了，只有真正深入了解后才是自己的。

另外Github Advanced Search 可以用来寻找小伙伴哦—— [Github Advanced Search猎头大法](http://wangchao.de/github-advanced-search%E7%8C%8E%E5%A4%B4%E5%A4%A7%E6%B3%95/).

未完待续…
