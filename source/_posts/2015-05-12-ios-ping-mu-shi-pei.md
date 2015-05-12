---
layout: post
title: "iOS屏幕适配"
date: 2015-05-12 13:36:34 +0800
comments: true
categories: iOS开发  
---  
###问题:  
今天在开发的过程中，遇到一个奇怪的问题：  
编写一个程序启动时的引导界面，用一个UIImageView控件加载一张图片作为背景，@1x图片分辨率为640\*960(像素)，@2x图片分辨率为640\*1136(像素)，@3x图片分辨率为750\*1334(像素)。  
在iphone4S上，如果背景尺寸设置为屏幕尺寸([[UIScreen mainScreen] bounds].size) ,那么@1x的图片会被压缩；如果背景尺寸设置为图片尺寸，则背景超出了屏幕范围；  
在iphone6 Plus上，如果背景尺寸设置为图片尺寸，则图片不能铺满整个屏幕。 
为了搞清楚这个问题的原因，去google了iOS界面适配方面的文章，终于明白了其中的原理，并确定解决方案。  

  
###原理:  

#####分辨率和像素    
经新xcode6模拟器验证()分辨率为pt，像素为真实pixel):  1.iPhone5分辨率320x568，像素640x1136，@2x   2.iPhone6分辨率375x667，像素750x1334，@2x     3.iPhone6 Plus分辨率414x736，像素1242x2208，@3x，（注意，在这个分辨率下渲染后，图像等比降低pixel分辨率至1080p(1080x1920)  

![图片][pic1]  
 
###解决方案:  

###参考：  
[iOS界面适配(三)](http://blog.csdn.net/houseq/article/details/40051207)  
[iphone屏幕适配，历史及现状](http://hjcapple.github.io/2014/10/10/iphone-screen.html):从历史说起，写的非常容易理解。  
[iOS开发中的各种尺寸](http://hjcapple.github.io/2014/12/14/ios-size.html):收藏，以方便查询   
[pic1]: http://cdn.cocimg.com/cms/uploads/allimg/140912/4196_140912103755_1.jpg “各型号iphone尺寸”  