# website-mobile-app
网站组移动端开发包

## 项目介绍

此为移动端基础开发框架，总体使用rem布局，原理可以参照这篇文章：<a href="http://www.w3cplus.com/mobile/lib-flexible-for-html5-layout.html">使用Flexible实现手淘H5页面的终端适配</a>，建议在用这个框架前学习这篇文章的知识，明白这个框架的原理

## 项目结构

- css 样式文件
- img 图片文件
- slice 雪碧图，工作流会在sass目录中生成_slice.scss，然后直接用**@extend %雪碧图名称**来引用，build之后就会自动生成雪碧图
- js js文件
- sass 项目使用sass开发
    - common 公用样式
        - reset.scss 样式重置文件，使用normalize.css和框架样式组合
    - module 样式库
        - ani.scss 动画库
    - index.scss 主样式文件
- tpl ejs模板，编辑html直接在这里编辑，由工作流输出html
- index.html

## 框架相关注意点

-  reset.scss中默认字体设置成设计稿宽度除以10，比如设计稿是750px，那么默认字体则设置成75px，如下
```
$browser-default-font-size: 75px !default;
```
- 设计稿中除了字体之外的所有元素的宽高，都直接用pxrem来代替，比如说设计稿中有一个元素是100px x 200px的尺寸，那么在sass中，代码如下
```
.example{
    width:pxrem(100px);
    height:pxrem(200px);
}
```
- 基本上，设计稿中的所有字体，用font-dpr来设置字体，比如设计稿中有字体大小为24px，那么代码如下
```
.example{
    @include font-dpr(24px);
}
```
- 增加微信分享功能，底部可以填充分享文案
```
    window.weixinConfig = {
        "title": "分享标题",
        "desc": "分享文案",
        "imgUrl": "img/mobile/share.jpg",
        "link": encodeURI(window.location.href.split("#")[0]),
        "type": "link",
        "dataUrl": null
    };
```
请记住微信分享一般分为朋友圈和好友分享两种，好友分享有**分享标题和分享文案**，而朋友圈分享一般只取**分享文案**


## 代码更新日志

1. 2016.7.26 - 修改工作流，由grunt变为gulp；增加微信分享功能