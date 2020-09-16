# Android图片轮播控件
[![Apache 2.0 License](https://img.shields.io/badge/license-Apache%202.0-blue.svg?style=flat)](http://www.apache.org/licenses/LICENSE-2.0.html)

##### 原作者不是我，因为原作者新开发了banner2.0的库，我只是接着继续写1.0版本的库而已。
##### 原作者：<a href="https://github.com/youth5201314" target="_blank">youth5201314</a>
##### 原作者新写的banner2.0版本：https://github.com/youth5201314/banner
##### 原作者之前的banner1.0版本：https://github.com/youth5201314/banner/tree/release-1.4.10

#### 以下是现版本的更新日志：
## 更新说明
#### v1.5.0
 * banner新增加属性：indicator_margin_bottom(设置指示器的bottom外边距)

#### 以下是之前原作者的更新日志：
## 更新说明
#### v1.4.10
    很久没有维护banner了，有工作原因比较忙，也有经常遇见一些素质低的人，感觉整个世界都欠他们的，特别影响心情。就放弃更新维护了，
    但是这半年每天邮箱都会收到各种建议反馈，也有很多人私信我，所以在此修复一些当前版本bug，
    关于有朋友要求让轮播类型可以自定义，不局限于imageview的需求，
    这个过段时间再发布一个全新的banner版本，会更加灵活，就不在原来的上面弄了，到时候分两个版本走！

 * 解决轮播手动滑动跳转问题：从第一张-->最后一张-->直接跳转到第二张
 * 解决update刷新轮播图崩溃问题
 * 将onPageScrolled和onPageSelected方法返回的position转成真实的position
 * 增加属性banner_default_image，设置当banner数据为空是显示的默认图片
 * 增加属性banner_layout，可以自定义布局文件，但是必须保证id的名称一样
 * 修改ViewPager偶发性的越界问题
 * SwipeRefreshLayout嵌套ViewPager的滑动冲突问题参考demo的SuperSwipeRefreshLayout类

#### v1.4.9
    banner 优化更新
 * 废弃以前的点击事件(当然还是可以使用以前的方法)，增加新的setOnBannerListener点击事件，下标从0开始
 * 解决update刷新轮播图后，会造成多次调用OnPageChangeListener的情况
 * 改变布局文件变量名，减少和工程冲突

#### v1.4.8
    banner 优化更新
 * 修改点击事件返回下标偶尔越界问题

#### v1.4.7
    banner 优化更新
 * 修复从第一个到最后一个，和从最后一个到第一个，数字和标题切换有点延迟的问题

#### v1.4.6
    banner 优化更新
 * 修改demo，更容易理解
 * 修复第一张过渡第二张图片切换时间翻倍问题
 * 图片默认全屏展示

#### v1.4.5
    banner 优化更新
 * 增加setViewPagerIsScroll(boolean isScroll)方法控制是否允许手动滑动轮播图，默认为true
 * 增加update()方法，方便更新图片
 * 解决最后一张图片切换到第一张，会出现卡顿(特别是不设置动画时有点明显)
 
#### v1.4.3-1.4.4
    banner bug修改
 * 轮播图变少时刷新崩溃问题
 * 增加控制图片显示属性 image_scale_type 的属性值（center，center_crop，center_inside，fit_center，fit_end，fit_start，fit_xy，matrix），和 ImageView 的效果一样
 * 当只有一张图片时不显示圆形指示器和数字指示器   
 
#### v1.4.2
    banner优化更新<感谢 694551594，FeverCombo3,MIkeeJY >
 * ！！！注意！！ImageLoader已从接口改变成抽象类，请调整下代码哦！
 * ImageLoader中增加ImageView控件创建方法createImageView()，可以满足fresco加载图片时扩展ImageView需求 
 * 修改关于banner刷新时需要第二轮才会更新图片问题(同title更新图片不更新问题)，具体看demo
 * 开放viewpager的setOffscreenPageLimit(int limit)方法
 * 优化banner在开始0s~20s之间会出现的内存泄漏问题
 * 优化最后一张到第一张之间滑动卡顿现象

#### v1.4.1
    bug修改<感谢深圳-放飞，台北-Tom>
 * 第一次加载一张图片(不能滑动[正常])-->刷新-->第二次加载多张图片(不能滑动[bug])
 * 滑动事件传递拦截优化
 * demo里添加了下拉刷新和RecyclerView添加头部的两种方式

#### v1.4
    全新升级，此次更新比较大，如果不习惯使用1.4的还是可以用1.3.3
 * 去掉app:default_image="默认加载图片"，需要可以自己在图片加载器中设置
 * 去掉glide图片加载相关代码全部用户自定义，外部通过实现（ImageLoader）去加载图片，尽力减少对第三方库的依赖
 * 去掉OnLoadImageListener图片加载监听事件，增加ImageLoader接口，通过setImageLoader设置图片加载器
 * 去掉isAutoPlay方法，改用startAutoPlay()|stopAutoPlay()这两个方法只能是渲染完（start()）后调用
 * 调整代码结构和执行顺序，由start()进行最后渲染和逻辑判断，前面方法可以随意调用打乱顺序。
 * 将设置图片和标题的方法改成setImages和setBannerTitles，传参方式改成集合，如果要用数组可以Arrays.asList()转成集合使用
 * 调整默认样式为CIRCLE_INDICATOR
 * 禁止单张轮播手动滑动问题
 * banner的标题文字单位指定为TypedValue.COMPLEX_UNIT_PX
 * demo改版，如果需要1.3.3的demo请在QQ群中下载
 

#### v1.3.3
    优化轮播首尾过渡时间
 * 再实现轮播从最后一张到第一张时，在第一张前面加了一张图片用于过渡，保证轮播不太生硬。这样也就造成了第一张时间有点长，
    开始没有发现，感谢大家的反馈，现在简单优化了下依然保留第一张500毫秒的时间用于过渡，让轮播保证流畅性。相信500毫秒的时间
    对于效果没有什么影响，这段时间很忙后面会对算法进行修改，目前先这样用着吧。

#### v1.3.2
    修复bug
 * 解决在自动轮播中，轮播中途触摸图片/左右移动时停止轮播，抬起不自动轮播问题
 
#### v1.3.1
    修复bug
 * app:delay_time="轮播间隔时间" 参数无用问题
 * 在暂停轮播时，当你手动滑动时会重新开始轮播问题
 * 在轮播中，当你按住轮播时暂停，松开后不会轮播问题
 
#### v1.2.9
    修复bug以及更新功能
 * app:image_scale_type="fit_xy,和imageview的ScaleType作用一样，不过只提供了两个常用的"
 * 修复设置动画后点击事件失效的问题。
 * 取消setScrollerTime设置方法

#### v1.2.8
    增加ViewPager的切换速度设置方法，以及动画的重新封装
 * 整理了17种viewpager过渡动画，并整理为常量方便调用，改变了传参格式，如果不够用可以自行自定义动画
 * 增加setScrollerTime(int duration)设置viewpager的切换速度,（单位毫秒，默认800）
 
#### v1.2.7
    增加viewpager的切换默认几种动画，和自定义动画方法
 * setBannerAnimation(int type)设置viewpager的默认动画
 * setPageTransformer(boolean reverseDrawingOrder, ViewPager.PageTransformer transformer)设置viewpager的自定义动画

#### v1.2.5
    修改bug
 * app:title_height="标题栏高度"，高度过小文字不显示问题
 
#### v1.2.4
    优化更新
 * app:title_background="标题栏的背景色"
 * app:title_height="标题栏高度"
 * app:title_textcolor="标题字体颜色"
 * app:title_textsize="标题字体大小"  
    
#### v1.2.3
    优化更新
 * 修复刷新banner从多张到1张时，还出现滑动的问题
 * demo增加功能
    
#### v1.2.2
    优化更新
 * 增加BannerConfig.CIRCLE_INDICATOR_TITLE_INSIDE显示圆形指示器和标题（水平显示）
 * 修改数字指示器时，变形问题。
 
#### v1.2.1
    优化更新
 * 修复NUM_INDICATOR和NUM_INDICATOR_TITLE模式下，没有轮播初始化为“1/1”的情况
 * 将图片加载默认图片取消，开发者可根据需要设置

#### v1.2.0
    优化更新
 * 修复小图片每次轮播被放大的问题
 * 开放了viewpager的滑动事件setOnPageChangeListener()
 * 增加触摸轮播图时暂停轮播，离开时继续轮播
 * 增加demo代码解释，关于刷新下标越界问题这个不存在，不懂的请看demo，
    不要一出问题就认为是banner的错，看看自己的用法是不是出来问题。
 
#### v1.1.9
    优化更新
 * 当图片为一张时，禁止轮播
 * 优化标题初始化速度
 
#### v1.1.8
    bug修改
 * 可能的存在的图片拉伸问题，替换为glide的图片加载大小计算
 * 修改关于非arraylist集合的强转问题。
 
#### v1.1.7
    应<wuzhaohui026>朋友的要求，做出更新
 * 为标题增加设置集合的方法：setBannerTitleList(List<String> titles)
 
#### v1.1.6
    综合大家的反馈，做出一些更新
 * 将代码的常量全部提出到BannerConfig类里了，以前的代码，大家需要修改下
 * 有人喜欢xml属性的方式来设置参数，那么增加了几个xml属性
     app:default_image="默认加载图片"
     app:delay_time="轮播间隔时间"
     app:is_auto_play="是否自动轮播"
 * 增加了设置glide加载方式的默认加载图片方法
     app:default_image="默认加载图片"
 * 重新写了一下demo，方便大家更加容易懂

#### v1.1.5
    感谢<imexception>朋友的反馈
 * 创建指示器初始化时默认的背景的添加，减少延迟等待更新
 * 优化指示器背景更新操作

#### v1.1.4
    更新内容
 * 增加setImages传参可以接收list集合
 * 优化在添加数据和创建指示器时的对象内存回收
 
#### v1.1.3
    修复了 <2316692710@qq.com> 朋友反馈的bug：
 * bug①  有标题的时候，向左滑动 ,会数组越界崩溃
 * bug②  指示器为数字的时候，向左滑动时会有一次显示为0/5
 
#### v1.1.2
    感谢 <cssxn@qq.com> 朋友提的意见，做出了如下更改：
 * 增加设置轮播图片，并且自定义图片加载方式:setImages(Object[] imagesUrl,OnLoadImageListener listener)
 * 增加设置图片加载事件，可以自定义图片加载方式:setOnBannerImageListener(this)
 
#### v1.1.1
    感谢 <969482412@qq.com> 朋友提的意见，做出了如下更改：
 * 增加圆形指示器的位置方法setIndicatorGravity(int type)
 * 增加设置是否自动轮播的方法isAutoPlay(boolean isAutoPlay)

#### v1.1.0  
    感谢 <997058003@qq.com> 朋友提的意见，做出了如下更改：
 * 修改指示器样式
 * 增加5种轮播样式，更加灵活方便的运用轮播控件，满足项目需求



