---
layout: post
title: "iOS开发问题集锦"
date: 2015-01-29 20:52:09 +0800
comments: true
categories: iOS开发
---
在iOS开发的过程中，遇到了不少坑，在这里，我把这些坑和对应的解决方法列出。

1.在iphone5s中，屏幕上下方有黑色空白。[解决方法](http://blog.csdn.net/tcthek/article/details/42674335)  

2.枚举一个数组的过程中，如果数组发生改变，会导致崩溃，崩溃信息如下：  
Exception Type:  EXC_CRASH (SIGABRT)
Exception Codes: 0x0000000000000000, 0x0000000000000000
Exception Note:  EXC_CORPSE_NOTIFY
Triggered by Thread:  0  
解决办法：枚举一个数组时，用copy拷贝一份进行枚举。

