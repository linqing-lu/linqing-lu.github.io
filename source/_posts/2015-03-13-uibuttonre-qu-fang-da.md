---
layout: post
title: "UIButton热区放大"
date: 2015-03-13 15:34:41 +0800
comments: true
categories: iOS小技巧
---  
今天遇到了UI指定的按钮大小小于苹果所规定的热区44\*44的情况，导致按钮很难点中，需要将热区放大；  
有[一种方法](http://itony.me/129.html)需要子类化UIButton，比较繁琐；  
另外一种方法是，将按钮的frame放大到热区大小(44\*44)，再通过setImageEdgeInsets改变按钮图片的显示大小为UI指定的大小即可，代码如下：  

{% codeblock lang:objective-c %}  
UIImage *btnImage = [UIImage imageNamed:@"random_pair_selection_cancel_mode"];  
CGFloat width = (btnImage.size.width >= 44 ? btnImage.size.width : 44);  
CGFloat height = (btnImage.size.height >= 44 ? btnImage.size.height : 44);  
_btnClose = [[UIButton alloc] initWithFrame:CGRectMake(0, 0, width, height)];  
[_btnClose setImage:btnImage forState:UIControlStateNormal];    
[_btnClose addTarget:self action:@selector(closeButton:) forControlEvents:UIControlEventTouchUpInside];  
CGRect frame = _btnClose.frame;  
frame.origin.x = SCREEN_WIDTH - 26 - btnImage.size.width;  
frame.origin.y = 41;  

//放大热区后，保持图片显示不变  
if (btnImage.size.width < width) {  
	width = (width - btnImage.size.width)/2;  
	height = (height - btnImage.size.height)/2;  
	[_btnClose setImageEdgeInsets:UIEdgeInsetsMake(height, width, height, width)];  
	//frame.origin.x = SCREEN_WIDTH - 26 - btnImage.size.width;  
	frame.origin.y = 41 - height;  
}

_btnClose.frame = frame;     
{% endcodeblock %}  

