# 移动端现状

## 目标

- 了解移动端web开发的问题
- 做开发的时候需要解决什么问题

## 知识内容

### 浏览器问题

```
   UC浏览器，QQ浏览器，欧朋浏览器，百度手机浏览器，360安全浏览器，谷歌浏览器，搜狗手机浏览器，猎豹浏览器，其他杂牌浏览器
    国内的UC和QQ，百度等手机浏览器都是根据Webkit修改过来的内核，国内尚无自助研发的内核，就像国内的手机操作系统都是基于Android修改的
```

### 设备屏幕问题

```
   大家都知道移动端设备屏幕尺寸非常多，碎片化严重。
   尤其是Android，你会听到很多种分辨率：480x800, 480x854, 540x960, 720x1280, 1080x1920，而且还有传说中的2K,4k屏。
   近年来iPhone的碎片化也加剧了：640x960, 640x1136, 750x1334, 1242x2208。
```

### 使用技术问题

```
移动web开发指的是需要适配移动设备的页面开发
移动web和桌面web没有本质的区别都使用css、html与js
```

### 主流设备尺寸

| 设备                    | 尺寸(英寸) | 开发尺寸(px) | 物理像素比(dpr) |
| --------------------- | ------ | -------- | ---------- |
| iphone3G              | 3.5    | 320*480  | 1.0        |
| iphone4/4s            | 3.5    | 320*480  | 2.0        |
| iphone5/5s/5c         | 4.0    | 320*568  | 2.0        |
| HTC One M8            | 4.5    | 360*640  | 3.0        |
| iphone6               | 4.7    | 375*667  | 2.0        |
| Nexus 4               | 4.7    | 384*640  | 2.0        |
| Nexus 5x              | 5.2    | 411*731  | 2.6        |
| iphone6 Plus          | 5.5    | 414*736  | 3.0        |
| Samsung Galaxy Note 4 | 5.7    | 480*853  | 3.0        |
| Sony Xperia Z Ultra   | 6.4    | 540*960  | 2.0        |
| Nexus 7 ('12)         | 7.0    | 600*960  | 1.3        |
| iPad Mini             | 7.9    | 768*1024 | 1.0        |

注：以上数据均参考 https://material.io/devices/ ,一个设备尺寸统计网站。  
注：作为前端开发不建议大家去纠结dp,dpi,pt,ppi等单位,因为它们有复杂的转换关系。

## 总结

移动web开发，也称之为H5开发，要迫切解决的问题不是技术，而是怎么去适配。

# 流失布局

## 目标

- 理解什么是流式布局
- 还有什么布局和流式布局类似

## 知识内容

### 流式布局

- **流式布局**,就是百分比布局,也称**非固定像素布局**。
- 通过盒子的宽度设置成百分比来根据屏幕的宽度来进行伸缩，不受固定像素的限制，内容向两侧填充。
- 这样的布局方式,是移动web开发使用的最常用布局方式。

### 伸缩布局

- CSS3引入了一种新的布局模式——**Flexbox布局**，即**伸缩布局盒模型**（Flexible Box），用来提供一个更加有效的方式制定、调整和分布一个容器里项目布局，即使它们的大小是未知或者动态的，这里简称为**Flex**。
- Flexbox布局常用于设计比较复杂的页面，可以轻松的实现屏幕和浏览器窗口大小发生变化时保持元素的相对位置和大小不变，同时减少了依赖于浮动布局实现元素位置的定义以及重置元素的大小。

## 总结

在屏幕设备尺寸不一致的情况下，使用非固定像素布局可以达到适配的目的，但是在移动端仅仅使用流失布局或者伸缩布局，还不够，因为受 **视口（viewport）** 影响。

# 标准视口

## 目标

- 构建移动端标准化页面
- 了解视口的常用参数设置

## 知识内容

### 视口概念

- 这是一个虚拟的区域，用来承载网页的区域，在浏览器可视窗口和网页之间。
- 有一些设备viewport的默认宽度是980px,网页内容显示在里面，为了能在320px屏幕内显示，会自动缩放。

在移动端有特殊的功能：可以设置宽度和高度，可以设置缩放比例，控制缩放的比例，控制用户是否可以自行缩放。

### 视口属性详解

| 属性            | 解释                                   |
| ------------- | ------------------------------------ |
| width         | 宽度设置的是viewport宽度，可以设置device-width特殊值 |
| initial-scale | 初始缩放比，大于0的数字                         |
| maximum-scale | 最大缩放比，大于0的数字                         |
| minimum-scale | 最小缩放比，大于0的数字                         |
| user-scalable | 用户是否可以缩放，yes或no（1或0）                 |

### 视口的具体应用

- 适配有三点事情需要去做：
  - 页面的宽度和设备样宽
  -  默认的缩放比例是1.0
  -  不允许用户去缩放页面
- 标准的viewport设置：
  - 视口宽度和设备保持一致
  - 视口的默认缩放比例1.0
  - 不允许用户自行缩放
  - 最大允许的缩放比例1.0
  - 最小允许的缩放比例1.0

```html
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
```



## 总结

移动端适配视口的标准设置是前提，虽然是标准设置，那其他设置是否也可以达到适配目的呢?

# 移动端二倍图

## 目标

- 什么是物理像素
- 什么是物理像素比
- 为什么需要使用二倍图

## 知识内容



### 移动端设备屏幕清晰度

- 物理像素点指的是屏幕显示的最小颗，是物理真实存在的。
- 所谓Retina是一种显示技术，可以将把更多的物理像素点压缩至一块屏幕里，从而达到更高的分辨率并提高屏幕显示的细腻程度。
- 而一个px的绝对（在开发中认为是绝对）长度能显示的物理像素点的个数，称为物理像素比，屏幕像素比。

![img](data:image/jpeg;base64,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Mrf/AOLrvfgP+yF8T/A3xg8K6/rGi29vplheCa4lW/hcquCM7QxJ69qVLD1lUi3B7roXmOd5ZUwVeEMTBtxkkuZb2fmfMHjr/kd/EP8A2Ebj/wBGtWHX0n4q/Yl+LeqeKNYvbfQbV7e4vJpo2OowDKs5IOC/HBrK/wCGFvjD/wBC/a/+DK3/APi6iWGrXfuP7jro57lapRTxMNl9pf5nD/s5f8l68Af9hq1/9GCsP4r/APJUvGP/AGGbz/0e9fQ/wZ/Y6+KXg74seEtc1TRLaDTtP1KC5uJFv4XKorgkgBsnjsKy/H/7FnxY17x34k1Oy0K2ks73Urm5hc6hApZHlZlOC2RwRxWv1et7JLke/byPOWdZZ/aLqfWYcvIlfmVr8z03PmKvVP2WP+ThfAn/AGEV/wDQWrqv+GFvjD/0L9r/AODK3/8Ai6734D/shfE/wN8YPCuv6xotvb6ZYXgmuJVv4XKrgjO0MSevappYesqkW4PddDbMc7yypgq8IYmDbjJJcy3s/M/QiiiivsD+XwooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigD//2Q==)

### 二倍图的使用

在标准的viewport设置中，使用二倍图来提高图片质量，解决在高清设备模糊问题。

```css
    .box{
        /*原始图片100*100px*/
        background-size: 50px 50px;
    }
    img{
        /*原始图片100*100px*/
        width: 50px;
        height: 50px;
    }
```

## 总结

在移动端屏幕的清晰度由物理像素比决定的，但是如果对于现实的图片质量不够，会造成图片模糊发虚现象，二倍图是决定这个问题的简单做法。


# 触摸事件

## 目标

- 掌握移动端触摸事件
- 掌握移动端滑动效果的实现

## 知识内容

### 触摸事件

| 事件          | 说明                    |
| ----------- | --------------------- |
| touchstart  | 当手指触碰屏幕时候触发该事件        |
| touchmove   | 当手指在屏幕上滑动时候触发该事件      |
| touchend    | 当手指离开屏幕时触发该事件         |
| touchcancel | 当系统停止跟踪（被迫终止）触摸时候会触发。 |

| 触摸点集合          | 说明              |
| -------------- | --------------- |
| targetTouches  | 目标元素的所有当前触摸点集合  |
| changedTouches | 目标元素的最新更改的触摸点集合 |
| touches        | 页面上的所有触摸点集合     |
注意：在touchend事件的时候event只会记录changedtouches

| 点坐标             | 说明        |
| --------------- | --------- |
| pageX/pageY     | 基于页面大小的坐标 |
| clientX/clientY | 基于视口大小的坐标 |
| screenX/screenY | 基于屏幕大小的坐标 |

### 滑动效果原理

```js
imageBox.addEventListener('touchmove', function (e) {
        var moveX = e.touches[0].clientX;
        distanceX = moveX - startX;
        /*计算将要给图片盒子的定位*/
        /*基于当前的定位去计算*/
        var translateX = -index * width + distanceX;
});
```



## 总结

移动端滑动效果，就是使用touch事件，拖动元素。

# 区域滚动

## 目标

- 使用区域滚动插件显示滑动效果
- 了解区域滚动的实现原理

## 知识内容

### 插件介绍

区域滚动插件，对于移动端的页面滚动效果表现不一致，和需要上拉刷新上拉加载等效果的页面，可以帮助快速的实现滚动效果。

### 插件使用

**IScroll是一个类，每个需要使用滚动功能的区域均要进行初始化**。每个页面上的iScroll实例数目在设备的CPU和内存能承受的范围内是没有限制的。

尽可能保持DOM结构的简洁。iScroll使用硬件合成层但是有一个限制硬件可以处理的元素。
最佳的HTML结构如下：

```html
<div id="wrapper">
    <ul>
        <li>...</li>
        <li>...</li>
        ...
    </ul>
</div>
```

iScroll作用于滚动区域的外层。在上面的例子中，UL元素能进行滚动。只有容器元素的第一个子元素能进行滚动，其他子元素完全被忽略。

最基本的脚本初始化的方式如下：

```html
<script type="text/javascript">
    var myScroll = new IScroll('#wrapper');
</script>
```

**第一个参数可以是滚动容器元素的DOM选择器字符串**，也可以是滚动容器元素的引用对象。下面是一个有效的语法：

```js
var wrapper = document.getElementById('wrapper');
var myScroll = new IScroll(wrapper);
```

所以基本上你要么直接传递元素，要么传递一个querySelector字符串。因此可以使用css名称代替ID去选择一个滚动器容器,如下:

```js
var myScroll = new IScroll('.wrapper');
```

> 注意，iScroll使用的是querySelector 而不是 querySelectorAll，所以iScroll只会作用到选择器选中元素的第一个。如果你需要对多个对象使用iScroll，你需要构建自己的循环机制。



### 参数配置

参考 http://www.mamicode.com/info-detail-331827.html

## 总结

在移动端的上拉刷新，下拉加载，区域滑动，可使用区域滚动插件快速实现。

# 手势事件

## 目标

- 了解是什么tap事件
- 了解什么是swipe事件

## 知识内容

### 轻触事件 tap

出现的原因：由于早期移动端页面双击可以缩放，为了检测双击操作，延长了click的响应时间，200-300ms。

第一种解决方案：
```javascript
        /*模拟tap事件（tap在移动端库zepto.js有使用）*/
        /*1. 响应的速度比click要快   150ms */
        /*2. 不能滑动*/
        var bindTapEvent = function (dom, callback) {
            var startTime = 0;
            var isMove = false;
            dom.addEventListener('touchstart', function () {
                startTime = Date.now();
            });
            dom.addEventListener('touchmove', function () {
                isMove = true;
            });
            dom.addEventListener('touchend', function (e) {
                if ((Date.now() - startTime) < 150 && !isMove) {
                    callback && callback.call(this, e);
                }
                startTime = 0;
                isMove = false;
            });
        }
```
第二种解决方案：
```html
<!--
1 使用一个叫：fastclick.js 提供移动端click响应速度的
2 下载：https://cdn.bootcss.com/fastclick/1.0.6/fastclick.min.js
3 使用：
-->
<script src="../js/fastclick.min.js"></script>
<script>
    /*当页面的dom元素加载完成 如果使用jquery $(function(){});*/
    document.addEventListener('DOMContentLoaded', function() {
        /*初始化方法*/
        FastClick.attach(document.body);
    }, false);
    /*正常使用click事件就可以了*/
</script>
```


### 滑动手势事件 swipe

手势事件：滑动，左滑，右滑，上滑，下滑 （swipe在移动端库zepto.js有使）

```javascript
        /*1. 理解移动端的手势事件*/
        /*2. swipe swipeLeft swipeRight swipeUp swipeDown */
        /*3. 左滑和右滑手势怎么实现*/
        var bindSwipeEvent = function (dom,leftCallback,rightCallback) {
            /*手势的条件*/
            /*1.必须滑动过*/
            /*2.滑动的距离50px*/
            var isMove = false;
            var startX = 0;
            var distanceX = 0;
            dom.addEventListener('touchstart',function (e) {
                startX = e.touches[0].clientX;
            });
            dom.addEventListener('touchmove',function (e) {
                isMove = true;
                var moveX = e.touches[0].clientX;
                distanceX = moveX - startX;
            });
            dom.addEventListener('touchend',function (e) {
                /*滑动结束*/
                if(isMove && Math.abs(distanceX) > 50){
                    if(distanceX > 0){
                        rightCallback && rightCallback.call(this,e);
                    }else{
                        leftCallback && leftCallback.call(this,e);
                    }
                }
                /*重置参数*/
                isMove = false;
                startX = 0;
                distanceX = 0;
            });
        }
        bindSwipeEvent(document.querySelector('.box'),function (e) {
            console.log('左滑手势');
        },function (e) {
            console.log('右滑手势');
        });
```


## 总结

移动端的一些手势事件都是由touch事件封装得来的，在一些移动端框架中会使用。

# 响应式布局

## 目标

- 理解什么是响应式
- 响应式的原理是什么

## 知识内容

### 响应式布局概念

- 在移动互联日益成熟的时候，我们在桌面浏览器上开发的网页已经无法满足移动设备的阅读。
- 通常的做法是针对移动端单独做一套特定的版本。
- 但是如果终端越来越多那么你需要开发的版本就会越来越多（大屏移动设备普及）。
- 那么Ethan Marcotte在2010年5月份提出的一个概念，简而言之，**就是一个网站能够兼容多个终端**。

### 响应式布局原理

CSS3中的Media Query（媒体查询）  
**通过查询screen的宽度来指定某个宽度区间的网页布局。**

| 划分设备     | 尺寸区间         |
| -------- | ------------ |
| 超小屏幕（手机） | 768px以下      |
| 小屏设备     | 768px-992px  |
| 中等屏幕     | 992px-1200px |
| 宽屏设备     | 1200px以上     |

```css
@media screen and (max-width: 768px){
  .container{
    width: 100%;
  }
}
@media screen and (min-width: 768px) and (max-width: 992px){
  .container{
    width: 750px;
  }
}
@media screen and (min-width: 992px) and (max-width: 1200px){
  .container{
    width: 970px;
  }
}
@media screen and (min-width: 1200px){
  .container{
    width: 1170px;
  }
}
```



### 对比针对移动端开发区别

| 开发方式 | 移动web开发+PC开发                    | 响应式开发                                 |
| ---- | ------------------------------- | ------------------------------------- |
| 应用场景 | 一般在已经有PC端的网站，开发移动站的时候，只需单独开发移动端 | 针对新建站的一些网站，现在要求适配移动端，所以就一套页面兼容各种终端，灵活 |
| 开发   | 针对性强，开发效率高                      | 兼容各种终端，效率低                            |
| 适配   | 只适配 移动设备，pad上体验相对较差             | 可以适配各种终端                              |
| 效率   | 代码简洁，加载快                        | 代码相对复杂，加载慢                            |

## 总结

移动web开发和响应式开发都是现在主流的开发模式。  
使用的都是流式布局，来适配不同设备。  
由于终端设备的多样化，新建站的站点会优先用响应式来开发。


# bootstrap

## 目标

- 掌握bootstrap的基本样式使用
- 掌握bootstrap的基本组件使用
- 能够使用bootstrap完成响应式页面

## 知识内容

### 什么是UI框架

user interface 用户界面，指的是有预制样式库，组件，插件，有一套比较完整的网页功能解决方案，称为UI框架

### bootstrap是什么

- 简介：  
    + 作者：Twitter  公司两位前端工程师（mark otto && jacob thornton）在2011发起开发完成的。
    + 特点：组件简洁大方，代码规范精简，界面自定义性强。
    + 目的：提高web开发效率。  
- 文档：  
    + 中文官网  http://www.bootcss.com/
    + 官网 http://getbootstrap.com/
    + 学习文档 http://bootstrap.css88.com/  
- 优点：  
    + 有自己的生态圈，不断的更新迭代。
    + 提供了一套简洁、直观、强悍的组件。
    + 标准化的html+css编码规范。
    + 让开发更简单，提高了开发的效率。
    + **注意：虽然界面组件样式已经定义好了，但是扩展性相对较强，也就是说我们还可以自定义，修改默认样式。**
- 版本:  
    + 2.x.x  停止维护,兼容性好,代码不够简洁，功能不够完善。
    + 3.x.x  目前使用最多,稳定,但是放弃了IE6-IE7。对IE8支持但是界面效果不好,偏向用于开发响应式布局、移动设备优先的 WEB 项目。

### bootstrap基本模板

````html
<!--h5文档申明-->
<!DOCTYPE html>
<!--文档语言申明  en zh-CN zh-tw -->
<html lang="zh-CN">
<head>
    <!--文档编码申明-->
    <meta charset="utf-8">
    <!--要求当前网页使用浏览器最高版本的内核来渲染-->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!--视口的设置：视口的宽度和设备一致，默认的缩放比例和PC端一致，用户不能自行缩放-->
    <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=0">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <!-- 优先加载和浏览器解释 -->

    <title>title</title>

    <!-- Bootstrap 核心样式-->
    <link href="../lib/bootstrap/css/bootstrap.css" rel="stylesheet">
    <!-- html5shiv 和  respond 分别用来解决IE8版本浏览器不支持 H5标签和媒体查询的  不兼容问题-->
    <!-- HTML5 shiv and Respond.js for IE8 support of HTML5 elements and media queries -->
    <!-- 警告：不能以file形式打开，本地打开。最好http://打开 -->
    <!-- WARNING: Respond.js doesn't work if you view the page via file:// -->
    <!-- 在 IE 9 一下引入-->
    <!--[if lt IE 9]>
    <script src="../lib/html5shiv/html5shiv.min.js"></script>
    <script src="../lib/respond/respond.min.js"></script>
    <![endif]-->
</head>
<body>
<!--TODO-->
<!-- bootstrap依赖jquery-->
<!-- jQuery (necessary for Bootstrap's JavaScript plugins) -->
<script src="../lib/jquery/jquery.min.js"></script>
<!-- bootstrap js 核心文件-->
<!-- Include all compiled plugins (below), or include individual files as needed -->
<script src="../lib/bootstrap/js/bootstrap.min.js"></script>
</body>
</html>
````
### bootstrap常用类

- container
- container-fluid
- row
- col-\*-\*
- col-\*-offset-\*
- col-\*-pull-\*
- col-\*-push-\*
- pull-left
- pull-right
- text-center
- text-left
- text-right

### 怎么使用组件

查询官方文档

- 组件的HTML模板代码结构分析
- 写一份和组件一致的样式选择器修改预制样式为产品需求样式
- 检查响应式是否符合产品需求，不满足自行修改

## 总结

bootstrap是一个完整的组件库，包含html,css,js的框架，能够快速的搭建响应式站点。

# less

## 目标

- 什么是预编译脚本语言less
- less的基本语法

## 知识内容

### 什么是less

作为一门标记性语言，CSS 的语法相对简单，对使用者的要求较低，但同时也带来一些问题：CSS需要书写大量看似没有逻辑的代码，不方便维护及扩展，不利于复用，尤其对于非前端开发工程师来讲，往往会因为缺少 CSS 编写经验而很难写出组织良好且易于维护的 CSS 代码，造成这些困难的很大原因源于 CSS 是一门非程序式语言，没有变量、函数、SCOPE（作用域）等概念。LESS 为 Web 开发者带来了福音，它在 CSS 的语法基础之上，引入了变量，Mixin（混入），运算以及函数等功能，大大简化了 CSS 的编写，并且降低了 CSS 的维护成本，就像它的名称所说的那样，LESS 可以让我们用更少的代码做更多的事情。

### less的安装

1. 安装nodejs https://nodejs.org/dist/ 可选择版本(6.0)。
2. 检查是否安装成功，使用cmd命令 node -v 查看版本即可。
3. 基于nodejs安装less:
    + 在线安装：使用cmd命令 npm install -g less
    + 离线安装:   
      a.找到C盘根目录下的用户或User文件夹打开  
      b.找到当前计算机使用的用户文件夹打开  
      c.找到隐藏文件夹AppData打开  
      d.找到Roaming文件夹打开  
      e.找到npm文件夹打开，该文件夹为基于nodejs程序目录  
      f.把npm.zip文件解压到该目录 
4. 基于koala软件也可以编译LESS;

### less编译

本质上，LESS 包含一套自定义的语法及一个解析器，用户根据这些语法定义自己的样式规则，这些规则最终会通过解析器，编译生成对应的 CSS 文件。LESS 并没有裁剪 CSS 原有的特性，更不是用来取代 CSS 的，而是在现有 CSS 语法的基础上，为 CSS 加入程序式语言的特性。

```text
    lessc 目标文件地址 生成文件地址
```
在开发过程当中如果要预览less，每次都要执行编译命令，为了方便可以使用部分编辑器中less自动编译功能。
1. 点击文件打开菜单，选择设置选项
2. 选择工具当中的文件监听选项
3. 点击右上角加号按钮，选择less后弹出对话框，点击确定即可。less的语法

### less基本语法

- 变量
```less
    @mainColor:#e92323;
    @className:box;
    
    div{
      background: @mainColor;
    }
    a:hover{
      color: @mainColor;
    }
    //变量用于字符拼接使用方法
    .@{className}{
      color: @mainColor;
    }
```
- 混入(mixin)
```less
    .borderRadius(@width:100px){
      border-radius: @width;
      -webkit-border-radius:@width;
      -moz-border-radius:@width;
      -o-border-radius:@width;
      -ms-border-radius:@width;
    }
```
- 嵌套
```less
    .wjs_app{
      display: block;
      img{
        display: none;
      }
      /*需要连接的情况：&*/
      &:hover{
        img{
          display: block;
          position: absolute;
          left: 50%;
          margin-left:-60px;
          border: 1px solid #ccc;
          border-top: none;
          top:40px;
          z-index: 100000;
        }
      }
      > div{
        display: block;
      }
    }
```
- 导入
```text
@import "variables";
```
- 运算&内置函数

api地址：http://lesscss.cn/functions/#functions-overview

中文：http://www.css88.com/doc/less/functions/#color-operations

```less
   /*运算*/
   @num:5;
   ul{
     width: 100%*@num;
     li{
       width: 100%/@num;
       color: red+yellow+blue;
       background: gray*0.3;
       /*内置函数*/
       border-color: darken(red,20%);
     }
   } 
```
### less预览

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <link rel="stylesheet" type="text/less" href="index.less">
    <script src="less.min.js"></script>
    <script>
        less.watch();
    </script>
</head>
<body>
    <!--1.在浏览器端直接使用less文件预览 type="text/less" -->
    <!--2.浏览器无法直接使用less类型的文件，无法解析-->
    <!--3.转换成css,需要js插件支持-->
    <!--4.下载插件 https://github.com/less/less.js/tree/master/dist -->
    <!--5.less.js会异步加载less文件的内容，再去解析成css,然后追加到style-->
    <!--6.必须使用HTTP形式打开页面，不要以file形式打开-->
    <!--7.更改完成之后每次要刷新，可以配置less监听，自动刷新页面预览-->
    <!--8.需要js配置 less.watch() -->
    <div class="box2">test</div>
</body>
</html>
```
## 总结

less是一门预编译脚本语法，使用它用来提高css的可维护性。

# rem适配方案

## 目标

- 掌握rem的适配原理
- 掌握rem+媒体查询适配方案
- 掌握rem+flexible.js适配方案

### 知识内容

### rem的适配原理

- rem 是相对于页面根源素html的字体大小的一个尺寸单位
- 页面内容可以使用rem为单位，那么html的字体大小就是一个控制尺寸的开关
- 当设备改变的时候可以根据设备的宽度和原本设计稿的尺寸比例关系设置html的字体大小
- 这样凡是以rem为单位的内容会根据设备做等比适配

```text
    1.假设设计稿是750px
    2.假设这个时候html字体大小为100px
    3.那么在320px设备的时候  字体大小为 100/750*320
    4.只要根据这个比例在不同设备设置rem基准值(html字体大小)即可
    5.改变rem基准值有两种方式：媒体查询或javascript
```
### rem+媒体查询

```css
/*假设的设备  320px 414px 640px */
@media (min-width: 320px) {
    html{
        font-size: 50px;
    }
}
@media (min-width: 414px) {
    html{
        font-size: 64.6875px;
    }
}
@media (min-width: 640px) {
    html{
        font-size: 100px;
    }
}
```
### rem+flexible.js

- flexible.js 是手机淘宝团队做移动端适配的库
- 我们使有它的目的只有一个根据设备设置rem基准值

```html
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=.0">
<script src="flexible.js"></script>
```
### 基于less的rem可维护方案

```less
//适配主流设备十几种
@adapterDeviceList:750px,720px,640px,540px,480px,424px,414px,400px,384px,375px,360px,320px;
//设计稿尺寸
@psdWidth:750px;
//预设基准值
@baseFontSize:100px;
//设备的种类
@len:length(@adapterDeviceList);
//适配函数
.adapterMixin(@index) when ( @index > 0){
  @media (min-width: extract(@adapterDeviceList,@index)){
    html{
      font-size: @baseFontSize / @psdWidth * extract(@adapterDeviceList,@index);
    }
  }
  .adapterMixin( @index - 1);
}
```
## 总结

使用rem完成页面的适配，注意不一定全部都是rem,大布局的适配还是可以使用流失布局或者伸缩布局。

# zepto.js

## 目标

- 能够使用zepto完成移动端操作
- 了解zepto的模块组成

## 知识内容

### zepto介绍

- Zepto是一个轻量级的针对现代高级浏览器的JavaScript库， 它与jquery有着类似的api。 如果你会用jquery，那么你也会用zepto。
- Zepto模块

| module     | default | description                              |
| ---------- | ------- | ---------------------------------------- |
| zepto      | ✔       | 核心模块；包含许多方法                              |
| event      | ✔       | 通过on()& off()处理事件                        |
| ajax       | ✔       | XMLHttpRequest 和 JSONP 实用功能              |
| form       | ✔       | 序列化 & 提交web表单                            |
| ie         | ✔       | 增加支持桌面的Internet Explorer 10+和Windows Phone 8。 |
| detect     |         | 提供 $.os和 $.browser消息                     |
| fx         |         | The animate()方法                          |
| fx_methods |         | 以动画形式的 show, hide, toggle, 和 fade*()方法.  |
| assets     |         | 实验性支持从DOM中移除image元素后清理iOS的内存。            |
| data       |         | 一个全面的 data()方法, 能够在内存中存储任意对象。            |
| deferred   |         | 提供 $.Deferredpromises API. 依赖"callbacks" 模块. 当包含这个模块时候, $.ajax() 支持promise接口链式的回调。 |
| callbacks  |         | 为"deferred"模块提供 $.Callbacks。             |
| selector   |         | 实验性的支持 jQuery CSS 表达式 实用功能，比如 $('div:first')和 el.is(':visible')。 |
| touch      |         | 在触摸设备上触发tap– 和 swipe– 相关事件。这适用于所有的`touch`(iOS, Android)和`pointer`事件(Windows Phone)。 |
| gesture    |         | 在触摸设备上触发 pinch 手势事件。                     |
| stack      |         | 提供 andSelf& end()链式调用方法                  |
| ios3       |         | String.prototype.trim 和 Array.prototype.reduce 方法 (如果他们不存在) ，以兼容 iOS 3.x. |

### 自定义打包

```text
1、首先在自己的电脑上要安装Node.js和npm包管理工具；
2、从github上下载zepto.js的源文件包到本地磁盘（例如：E:\Learning\JS）；地址：https://github.com/madrobby/zepto
3、将下载的zepto压缩包解压，进入，找到make文件，打开，找到第42行的位置，添加需要的模块名称（这里增加了fx_methods 和 fx 模块），以空格做分隔；  
modules = (env['MODULES'] || 'zepto event ajax form ie').split(' ')
4、运行中，cmd打开命令窗口，并进入zepto文件目录；
5、执行 npm install 命令；
6、输入npm run-script dist 命令，进行构建；
```
## 总结

zepto就是jquery的轻量版，功能差不多，但是不完全覆盖。


#  swiper

## 目标

- 使用swiper解决移动端轮播图需求

## 知识内容

### 介绍

**Swiper**是纯javascript打造的滑动特效插件，面向手机、平板电脑等移动终端。

**Swiper**能实现触屏焦点图、触屏Tab切换、触屏多图切换等常用效果。

**Swiper**开源、免费、稳定、使用简单、功能强大，是架构移动终端网站的重要选择！

### 使用

# Swiper4.x使用方法

1.首先加载插件，需要用到的文件有swiper.min.js和swiper.min.css文件。可下载[Swiper文件](http://www.swiper.com.cn/download/index.html#file1)或使用[CDN](http://www.swiper.com.cn/cdn/index.html)。

```
<!DOCTYPE html>
<html>
<head>
    ...
    <link rel="stylesheet" href="path/to/swiper.min.css">
</head>
<body>
    ...
    <script src="path/to/swiper.min.js"></script>
</body>
</html>
```

2.HTML内容。

```
<div class="swiper-container">
    <div class="swiper-wrapper">
        <div class="swiper-slide">Slide 1</div>
        <div class="swiper-slide">Slide 2</div>
        <div class="swiper-slide">Slide 3</div>
    </div>
    <!-- 如果需要分页器 -->
    <div class="swiper-pagination"></div>
    
    <!-- 如果需要导航按钮 -->
    <div class="swiper-button-prev"></div>
    <div class="swiper-button-next"></div>
    
    <!-- 如果需要滚动条 -->
    <div class="swiper-scrollbar"></div>
</div>
导航等组件可以放在container之外
```

3.你可能想要给Swiper定义一个大小，当然不要也行。

```
.swiper-container {
    width: 600px;
    height: 300px;
}  
```

4.初始化Swiper：最好是挨着</body>标签

```
<script>        
  var mySwiper = new Swiper ('.swiper-container', {
    direction: 'vertical',
    loop: true,
    
    // 如果需要分页器
    pagination: {
      el: '.swiper-pagination',
    },
    
    // 如果需要前进后退按钮
    navigation: {
      nextEl: '.swiper-button-next',
      prevEl: '.swiper-button-prev',
    },
    
    // 如果需要滚动条
    scrollbar: {
      el: '.swiper-scrollbar',
    },
  })        
  </script>
</body>
```

如果不能写在HTML内容的后面，则需要在页面加载完成后再初始化。

```
<script type="text/javascript">
window.onload = function() {
  ...
}
</script>
```

或者这样（Jquery和Zepto）

```
<script type="text/javascript">
$(document).ready(function () {
 ...
})
</script>
```

5.完成。恭喜你，现在你的Swiper应该已经能正常切换了。

6.参考地址 http://www.swiper.com.cn/api/index.html

## 总结

移动端轮播图需求使用swiper来解决是一个好的选择。