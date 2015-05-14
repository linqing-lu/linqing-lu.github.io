---
layout: post
title: "iOS开发入门指南"
date: 2015-05-14 21:56:27 +0800
comments: true
categories: iOS开发  
---  
###概述  
我在转到iOS开发之前，一直做的是windows上的C++开发，用了一段时间的MFC，一段时间的Qt.转入iOS也没碰到太大的难题。本文主要根据我的学习经历进行总结，希望能对其他入门者有点参考价值。  

###入门  
首先要会使用mac的操作系统，越熟练越好。各种快捷键，各种软件安装和配置等等。 
其次要会使用xcode，了解它的主要菜单项，各种快捷键。然后新建一个iOS工程，区分Project和Target，认真理解Build Settings,Build phases,Build Rules,General,Capabilities,Info中，主要配置项的意义。 
然后编写一个简单的程序，学习将程序运行在模拟器中，调试程序。如果要运行在真机中，需要有证书，个人开发者需要自己花费99美元，企业开发者可以利用公司的证书。
还得了解基本的Objective-C语法，因为我做了很长时间的C++开发，所以没花多少时间去专门学习Objective-C的语法，仅仅了解了 AClass *a = [[AClass alloc] init]这句话的含义就开始写demo练习了。当然，需要知道Objective-C的类是由哪些部分构成的，类的继承关系等等。@property/@protocol/@class/@interface/@implemetion等关键词的作用。    
现在苹果的swift已经出来了一年了，如果是个人开发者，可以从swift开始进行学习。   
理解Objectiv-c的内存管理，ARC和MRC的区别和联系，retain、assign、copy、strong、weak等关键词的含义；

###核心框架  
#####Foundation  

#####CocoaTouch  


###编写demo  
学习编程的最好方式就是动手实践，所以入门时可以有针对性的选择做一个demo进行练习，对于demo的选择，如果是自己心里早就想实现某个具有某些功能的app，那么就直接动手去实现它。否则的话，建议从以下几个方面进行考虑：  
1、练习UITableView控件的使用；  
2、练习UIControllerView的使用，主要是掌握MVC以及衍生的MVVM等框架，UIControllerView之间的跳转等等；  
3、编写iOS app的界面，可以使用storyboard和代码两种方式，对于入门者来说，如果不是为了很快做出一个app，而是想深入学习iOS开发的方方面面，建议采用代码编写界面的方式。  
4、(待补充)  

###学习开源库  
学习各种开源库的使用，首先掌握以下几个：  
1、AFNetworking，只要app涉及到网络，一般都会选择使用它；  
2、SDWebImage;  
3、...  

###推荐博客  
[唐巧的技术博客](http://devtang.com/blog/categories/ios/):很多干货，作者写的通熟易懂。    
[objc中国](http://objccn.io):为中国Objective-C社区带来最佳实践和先进技术,翻译的国外的objc.io的文章，同样干货满满。    
[casatwy.com](http://casatwy.com)  
[喵神的博客](http://onevcat.com)  
[全面理解iOS开发中的ScrollView](http://mobile.51cto.com/hot-430409.htm):详细描述了ScrollView实现的原理，并点拨了实现下拉刷新、避免键盘遮住有效区域的原理。  
[iOS应用架构谈：开篇](http://casatwy.com/iosying-yong-jia-gou-tan-kai-pian.html):一个架构师关于架构的观点，值得仔细揣摩  
[iOS应用架构谈：view层的组织和调用方案](http://casatwy.com/iosying-yong-jia-gou-tan-viewceng-de-zu-zhi-he-diao-yong-fang-an.html):作者写的很用心，看了一遍后收获很大，值得多看几遍然后参照进行实践，期待作者的后续文章。本文中还介绍了其他几篇相关好文，也很值得看。 
 
###学习技巧  
“平时学习控件，按照，继承关系、生命周期、内存管理、常用场景、个性定制、常见的坑。按照这个写个小博文。可能会好一些。” ，这是[知乎](http://www.zhihu.com)上一个用户说的，很有指导意义。    







