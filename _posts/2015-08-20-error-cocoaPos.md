---
layout: post
title: iOS－[!] Unable to find a specification for `*******`的错误解决
date: 2015-10-8 13:45:12
category: "iOS"
---

相信大家pod第三方库的时候经常遇到这种错误。。
可用下面👇方法解决：

把当前Pod的目录清理一下就行了。在终端执行以下命令：
	    
	pod repo remove master
	pod setup
	
setup成功后执行install

	pod install