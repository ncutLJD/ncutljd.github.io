---
layout: post
title:  "Springboot对配置文件的读取顺序"
categories: springboot
tags:  springboot
author: lijd
---

* content
{:toc}

###Springboot对配置文件的读取顺序

如果在不同的目录中存在多个配置文件，它的读取顺序是：
1. config/application.properties (项目根目录中config目录下)
2. config/application.yml
3. application.properties (项目根目录下)
4. application.yml
5. resources/config/application.properties (项目resources目录中config目录下)
6. resources/config/application.yml
7. resources/application.properties (项目的resources目录下)
8. resources/application.yml

![加载顺序1](http://129.204.42.126/images/springboot%E5%8A%A0%E8%BD%BD%E9%A1%BA%E5%BA%8F1.png)

![加载顺序1](http://129.204.42.126/images/springboot%E5%8A%A0%E8%BD%BD%E9%A1%BA%E5%BA%8F2.png)
