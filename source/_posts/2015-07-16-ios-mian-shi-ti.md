---
layout: post
title: "iOS面试题"
date: 2015-07-16 11:50:50 +0800
comments: true
categories: iOS开发  
---  
[参考文章](http://mp.weixin.qq.com/s?__biz=MjM5NTIyNTUyMQ==&mid=208981739&idx=1&sn=c5001053ef521375a9ab553dbc6a8d47#rd)：这篇文章中提到一些iOS面试题，把这些题的答案都搞明白了，对iOS开发的理解也会理解的更透彻，本文摘取其中一部分回答。  

1. <b>[※]@property中有哪些属性关键字？  
	A:</b> atomic(默认)，nonatomic；retain, copy, assign(默认); strong(ARC下默认), weak; readonly, readwrite(默认);  
	[参考文章1](http://www.linuxidc.com/Linux/2014-03/97744.htm)  
	[参考文章2](http://blog.csdn.net/dqjyong/article/details/7668601)  
2. <b>[※]weak属性需要在dealloc中置nil么?  
	A:</b> 当strong类型的指针被释放掉之后，所有的指向同一个对象的weak指针都会被清零。所以不需要中dealloc中置nil；  
	ARC里面的dealloc方法和MRC手动内存管理的区别在于。ARC里面不能调用super方法。ARC里面的dealloc一般用来注销NSNotification或者timer之类的实例。如果是类里面的强引用，可以在didReceiveMemoryWarning置于nil;

3. <b>[※※]@synthesize和@dynamic分别有什么作用？  
	A:</b>@synthesize实际的意义就是 自动生成属性的setter和getter方法。  
	@dynamic 就是要告诉编译器，代码中用@dynamic修饰的属性，其getter和setter方法会在程序运行的时候或者用其他方式动态绑定，以便让编译器通过编译。其主要的作用就是用在NSManagerObject对象的属性声明上，由于此类对象的属性一般是从Core Data的属性中生成的，core data 框架会在程序运行的时候为此类属性生成getter和setter方法。

4. <b>[※※※]ARC下，不显示指定任何属性关键字时，默认的关键字都有哪些？
	A:</b> atomic, strong, readwrite

5. <b>[※※※]用@property声明的NSString（或NSArray，NSDictionary）经常使用copy关键字，为什么？如果改用strong关键字，可能造成什么问题？
	A:</b>copy关键字表示拥有不同的内存空间，存放的时同样的内容，对一处的修改不会影响到另一处；strong关键字表示指针指向的内存空间时同一处，只是引用计数增加，对一个指针所指内容的修改会影响另一个指针。

6. [※※※]@synthesize合成实例变量的规则是什么？假如property名为foo，存在一个名为_foo的实例变量，那么还会自动合成新变量么？
7. [※※※※※]在有了自动合成属性实例变量之后，@synthesize还有哪些使用场景？
8. [※※]objc中向一个nil对象发送消息将会发生什么？ 
	A:什么也不会发生，不会崩溃，也不会接收对应的消息。
	
9. [※※※]objc中向一个对象发送消息[obj foo]和objc_msgSend()函数之间有什么关系？  
	A:[参考此文](http://imhehe.lofter.com/post/1d0d0dea_60691be)

10. [※※※]什么时候会报unrecognized selector的异常？  
	A: 发送消息是通过 objc_send(id, SEL, ...) 来实现的，它会首先在对象的类对象的 cache，method list 以及父类对象的 cache, method list 中依次查找 SEL 对应的 IMP；如果没有找到且实现了动态方法决议机制就会进行决议，如果没有实现动态方法决议机制或决议失败且实现了消息转发机制就会进入消息转发流程，否则程序 crash。也就是说如果同时提供了动态方法决议和消息转发，那么动态方法决议先于消息转发，只有当动态方法决议依然无法正确决议 selector 的实现，才会尝试进行消息转发。
11. [※※※※]一个objc对象如何进行内存布局？（考虑有父类的情况）
12. [※※※※]一个objc对象的isa的指针指向什么？有什么作用？
	A: Objective-C中的Object是一个结构体(struct)，第一个成员是isa，指向自己的class。这是在objc/objc.h中定义的。  
<pre><code>
typedef struct objc_object {
    Class isa;
} *id;
</pre></code>  
13. [※※※※]下面的代码输出什么？  
<pre><code>
@implementation Son : Father
- (id)init
{
    self = [super init];
    if (self) {
        NSLog(@"%@", NSStringFromClass([self class]));
        NSLog(@"%@", NSStringFromClass([super class]));
    }
    return self;
}
@end
</code></pre>  
14. [※※※※]runtime如何通过selector找到对应的IMP地址？（分别考虑类方法和实例方法法）
15. 15. [※※※※]使用runtime Associate方法关联的对象，需要在主对象dealloc的时候释放么？
16. [※※※※※]objc中的类方法和实例方法有什么本质区别和联系？
17. [※※※※※]_objc_msgForward函数是做什么的，直接调用它将会发生什么？
18. [※※※※※]runtime如何实现weak变量的自动置nil？
19. [※※※※※]能否向编译后得到的类中增加实例变量？能否向运行时创建的类中添加实例变量？为什么？
20. [※※※]runloop和线程有什么关系?
21. [※※※]runloop的mode作用是什么？
22. [※※※※]以+ scheduledTimerWithTimeInterval...的方式触发的timer，在滑动页面上的列表时，timer会暂定回调，为什么？如何解决？
23. [※※※※※]猜想runloop内部是如何实现的？
24. [※]objc使用什么机制管理对象内存？
25. [※※※※]ARC通过什么方式帮助开发者管理内存？
26. [※※※※]不手动指定autoreleasepool的前提下，一个autorealese对象在什么时刻释放？（比如在一个vc的viewDidLoad中创建）
27. [※※※※]BAD_ACCESS在什么情况下出现？
28. [※※※※※]苹果是如何实现autoreleasepool的？
29. [※※]使用block时什么情况会发生引用循环，如何解决？
30. [※※]在block内如何修改block外部变量？
31. [※※※]使用系统的某些block api（如UIView的block版本写动画时），是否也考虑引用循环问题？
32. [※※]GCD的队列（dispatch_queue_t）分哪两种类型？
33. [※※※※]如何用GCD同步若干个异步调用？（如根据若干个url异步加载多张图片，然后在都下载完成后合成一张整图）
34. [※※※※]dispatch_barrier_async的作用是什么？
35. [※※※※※]苹果为什么要废弃dispatch_get_current_queue？
36. [※※※※※]以下代码运行结果如何？
<pre><code>
- (void)viewDidLoad
{
    [super viewDidLoad];
    NSLog(@"1");
    dispatch_sync(dispatch_get_main_queue(), ^{
        NSLog(@"2");
    });
    NSLog(@"3");
}
</code></pre>
37. [※※]addObserver:forKeyPath:options:context:各个参数的作用分别是什么，observer中需要实现哪个方法才能获得KVO回调？
38. [※※※]如何手动触发一个value的KVO
39. [※※※]若一个类有实例变量NSString *_foo，调用setValue:forKey:时，可以以foo还是_foo作为key？
40. [※※※※]KVC的keyPath中的集合运算符如何使用？
41. [※※※※]KVC和KVO的keyPath一定是属性么？
42. [※※※※※]如何关闭默认的KVO的默认实现，并进入自定义的KVO实现？
43. [※※※※※]apple用什么方式实现对一个对象的KVO？
44. [※※]IBOutlet连出来的视图属性为什么可以被设置成weak?
45. [※※※※※]IB中User Defined Runtime Attributes如何使用？
46. [※※※]如何调试BAD_ACCESS错误
47. [※※※]lldb（gdb）常用的调试命令？
