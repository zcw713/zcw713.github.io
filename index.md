编译原理 -> 数据结构 -> C -> 内存 - > iOS实现原理

计算机基础 -> 编译原理 -> 内存 ->    iOS底层

页面渲染原理 -> 图片、视频加载 -> View加载与绘制 -> 事件

### [编译原理](https://zcw713.github.io/source/pages/%E7%BC%96%E8%AF%91)
- [Mach-O详解](https://zcw713.github.io/source/%E7%BC%96%E8%AF%91/Mach-O%E8%AF%A6%E8%A7%A3)
- [编译流程](https://zcw713.github.io/source/pages/%E7%BC%96%E8%AF%91)
- iOS编译原理，涉及到的编译过程：预处理、编译器、汇编器、链接器；
- iOS编译对应的Xcode中build settings配置；
- 什么是mach.o文件，app包里有哪些mach.o文件；
- ipa生成过程；
- 启动加速，pre main过程，main过程，main之后；
- 什么是静态库、动态库，以及他们如何被加载；

### [内存](https://zcw713.github.io/source/pages/%E5%86%85%E5%AD%98)
- 程序是如何被装载进内存，内存分配方式；
- 虚拟内存；
- iOS内存管理；
- 阐述一个nil对象从interface bulider产生，到载入程序运行空间，最后被释放时所经历的生命周期

### [iOS 证书](https://zcw713.github.io/source/pages/iOS%E8%AF%81%E4%B9%A6)
- 什么是RSA加密；
- iOS的签名证书机制；

### [iOS底层原理](https://zcw713.github.io/source/pages/%E7%BD%91%E7%BB%9C%E7%9B%B8%E5%85%B3)
- block内存布局， block的isa存储：方式，优缺点，你会选哪种多线程：有哪些，优缺点
- Runtime
- 内存管理：isa，weak实现
- arc/mrc是啥，ARC 在编译时做了哪些工作
- 崩溃的情况，数组越界为什么会崩溃，重复释放为什么会崩溃，app内存过大崩溃，怎么发现，怎么解决，自动释放池原理、自动释放池与ARC、自动释放池释放时机、
- 被放入到@autuReleasePool的对象，当自动释放池调用drain方法时，一定会释放吗
- @aotuReleasePool的嵌套使用，对象内存是如何被释放的
- 在Masonry的block中，使用self，会造成循环引用吗
- 线程：group和notify的使用，线程安全怎么解决，队列和线程的关系，
- GCD执行原理，在Runloop中的使用
- 一个变量，怎么实现同步读，异步写、利用iOS的多线程技术对共享变量实现多读单写操作
- 锁UI：autolayout和frame优缺点，原理
- 自旋锁和互斥锁的区别
- 解决网络请求的依赖关系：当一个接口的请求需要依赖于另一个网络请求的结果
- 子线程中如何管理对象的生命周期
- 线程之间的通信步骤
- unix上进程怎么通信
- runloop是什么，么时候运行、什么时候返回、怎么保活、会休眠？
- AFNetworking 中运用 Runloop，AFNetworking做了什么性能方面的优化
- RunLoop三种模式的区别、使用RunLoop的情况
- 消息转发机制
- property作用
- 响应链是怎么工作
- JSON转Model
- TableView优化，怎么减少卡顿、离屏渲染、检测卡顿、异步绘制原理
- 视频文件太大，要怎么上传、怎么断点续传
- app启动的详细过程、要优化怎么做、记录app启动速度
- 动态lib和静态lib区别、原理、何影响启动速度的
- category 是如何影响启动速度的、extension呢
- category复写元类方法原理
- 图片压缩与视频压缩、图片解码、渲染图片优化
- Pod update和pod install的区别
- 抓包工具抓取HTTPS的原理
- isEquel和hash的关系
- bitmap的结构
- 可变数组的实现原理
- 如何hook一个对象的方法，而不影响其它对象
- KVO、KVC，手动触发KVO
- notification是同步还是异步、kvo是同步还是异步、notification是全进程空间的通知吗、kvo呢
- 是否可以把比较耗时的操作放在NSNotificationCenter中
- @weakify和我们宏定义的WeakSelf有什么区别
- id 和 instanceType 区别
- self和super的区别
- 检测图层混合
- UI绘制原理
- UIView和CALayer之间的关系、从设计原则的角度回答系统为何这样设计
- UIView、CoreAnimation和CoreGraphics的关系
- UI卡顿、掉帧的原理
- 利用TableView的重用机制实现一个字母索引条
- 给系统对象如UIView增加属性
- Load Initialize区别
- Swift和Objective C区别、Swift可以和C++混编吗、class和struct有什么区别
- JSPatch的原理以及苹果如何检测
- UIscrollVew用到了什么设计模式、还能再foundation库中找到类似的吗
- 收到内存警告时应该怎么处理
- NSDictionary的实现，以及复杂度
- NSTimer如果重复调用怎样解除循环引用
- iOS有几种复制、什么行为能够产生深复制、复制的应用
- 怎么理解JSBridge工作的、这种工作原理有什么缺点吗
- SegmentFault、StackOverFlow在iOS中是什么错误
- 从浏览器查询一个关键字，从计算机原理到计算机网络，展示整个过程

### [网络](https://zcw713.github.io/source/pages/%E7%BD%91%E7%BB%9C%E7%9B%B8%E5%85%B3)
- 网络分层架构；
- TCP/IP原理；
- TCP如何保证可靠传输，分别有哪些机制
- TCP的慢启动特点
- tcp怎么识别get请求，异步阻塞
- 简要说明下用于交换网络的设备，从物理层往上进行叙述
- 数据链路层的帧的概念和作用
- ARP路由协议
- 传输层有哪些协议
- Socket原理，粘包处理；
- http是基于socket怎么实现的
- Https、Http区别，HTTP请求头和响应头、Cookie
- 解决DNS劫持
- AFN
- 大文件处理，断点续传；
- SDWebImage、NSCache、设计一个缓存器、实现LRU
- 如何查找两个子视图的共同父视图？

### [算法](https://zcw713.github.io/source/pages/%E9%80%9A%E7%94%A8)
- 不用临时变量怎么实现swap(a, b)--用加法或者异或都可以
- 二维有序数组查找数字--剑指offer第3题
- 亿级日志中，查找登陆次数最多的十个用户--剑指offer第30题
- 简述排序算法——快排partion函数的原理，堆排（不稳定），归并排序，基数排序。
- 算法字符串翻转
- NC24 删除有序链表中重复的元素-II [链接](https://zcw713.github.io/source/pages/%E9%80%9A%E7%94%A8)
- RLE算法，编写一个函数，实现统计字符次数的功能：例如输入为aaabbccc，输出为a3b2c3。不限语言
- 实现一个函数，用来判断一颗二叉树是不是对称的。注意，如果一个二叉树同此二叉树的镜像是同样的，定义其为对称的
- 无序数组中的中位数(快排思想)
- 给定一个整数数组和一个目标值，找出数组中和为目标值的两个数。
- NC71 旋转数组的最小数字 [链接](https://www.nowcoder.com/practice/9f3231a991af4f55b95579b44b7a01ba?tpId=117&&tqId=23269)
- 在数组中寻找第k大的数
- 判断一个链表是否有环
- 判断一个环的入口
- 用两个栈模拟一个队列
- 打印100到200之间的素数
- 反转链表
- 三种方式遍历二叉树
- 封装一个字符串逆序的API
- 求数组中和为某个值的所有子数组，比如数组是[5,5,10,2,3]一共有四个子数组的和是15

### [设计](https://zcw713.github.io/source/pages/%E9%80%9A%E7%94%A8)
- 一个email应用，简化版的outlook，只有message和contacts两个tab，需要设计一个架构，让API读的数据，能及时给到tabs里
- 在Xcode上运行了一个contacts页面：上方一个左右滚动的collectionView，下方一个上下滚动的tableView，这俩东西是联动的。他在代码里设置了很多可以改善的地方，都和TableView，CollectionView，ScrollView的操作相关
- 如何避免if else
- 微服务架构设想
- 进行项目瘦身
- 设计一个时长统计框架
- 设计一个图片缓存框架
- 客户端的整体架构实现是怎样的，解耦方式有哪些

### [通用](https://zcw713.github.io/source/pages/%E9%80%9A%E7%94%A8)
- 编码方式，unicode、utf-8；
- Base64、md5作用；
- hash冲突
- mimeType作用；
- 对称加密和非对称加密的区别
