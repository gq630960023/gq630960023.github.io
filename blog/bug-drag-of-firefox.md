<!--
author: wangjian
date: 2016-11-17
title: 火狐浏览器下拖拽插件无法拖拽的bug
tags: bug,火狐 
category: bug
status: publish
summary: 
web开发中遇到的各种奇葩bug
-->

折腾了一整天做了个拖拽排序的jquery效果，却发现在龙哥的火狐浏览器下无法拖拽，顿时很郁闷，抱着试试看的心态问了问度娘，查了好久终于找到相关的解决方案。

这应该是火狐浏览器自带的一个拖拽功能，会拖出一个重影，然后再干点其他的。。。

个人感觉火狐这功能很鸡肋，可以算的上是一个bug了。

解决方案如下：


	var cleanUpDefaultEvent = function (event) {
        event = event || window.event || arguments.callee.caller.arguments[0];
        if (event.preventDefault) {//IE not have
            event.preventDefault();
        }
        event.returnValue = false;
    };
 
    $('').mousedown(function(e) {
        cleanUpDefaultEvent(e)
        //do something
    })

定义一个`cleanUpDefaultEvent`的方法，然后在`mousedown`鼠标点击下去拖拽的时候执行就可以了，火狐下就正常了。

记录一下，以供查阅。

相关参考：[链接](http://blog.csdn.net/hw1287789687/article/details/51783320 "参考链接")

