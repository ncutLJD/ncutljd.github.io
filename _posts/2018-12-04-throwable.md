---
layout: post
title:  "Exception和Error"
categories: Java核心技术36讲
tags:  Java exception
author: ljda
---

* content
{:toc}


## 前言

在我们编写程序的时候，总会跟异常做斗争。不管你的程序多么完美，但最终还是会出现异常。而java也提供了对异常处理机制，因为这种处理的机制大大降低了编写和维护可靠程序的门槛。那么我们就了解下关于java的异常。
##  课程目录

- ClassNotFoundException发生在装入阶段。

 当应用程序试图通过类的字符串名称，使用常规的三种方法装入类，但却找不到指定名称的类定义时就抛出该异常。

- NoClassDefFoundError： 当目前执行的类已经编译，但是找不到它的定义时

也就是说你如果编译了一个类B，在类A中调用，编译完成以后，你又删除掉B，运行A的时候那么就会出现这个错误
