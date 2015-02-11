---
layout: post
title: "Core Animation编程指南要点集锦"
date: 2015-02-11 17:25:40 +0800
comments: true
categories: 
---
##1 在UIView中初始化动画
如果你想使用Core Animation初始化动画，你必须在一个基于视图的动画块内部执行所有Core Animaiton调用。UIView类默认是关闭图层动画的，你在动画块之外所做的改变都不是动画，但是你可在动画块中重新启用图层动画。清单3-5展示了一个关于如何隐式改变图层opacity和显式改变图层的position例子，在例子中myNewPosition变量被事先计算并被块所捕获。两个动画都开始于相同的时间，但透明度动画使用默认的定时，而位置动画使用动画对象指定的定时。
