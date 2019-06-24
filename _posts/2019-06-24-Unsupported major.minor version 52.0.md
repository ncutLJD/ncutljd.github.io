---
layout: post
title:  "Unsupported major.minor version 52.0"
categories: java
tags:  java jdk
author: lijd

---

* content
{:toc}

### 问题描述
- 启动项目后编译class文件会报下面的错误
```
java.lang.UnsupportedClassVersionError: msds/microservices/hub/api/service/PaymentHubService : Unsupported major.minor version 52.0 (unable to load class msds.microservices.hub.api.service.PaymentHubService)
```

### 问题分析
- 首先，需要理解java.lang.UnsupportedClassVersionError异常，UnsupportedClassVersionError顾名思义，Class版本不支持错误，那么版本问题，就是项目编译Class的JDK版本环境与运行的虚拟机JDK版本环境不一致。
- 根据错误信息可以知道Unsupported major.minor version 52.0，version 52.0正是对应了JDK1.8的版本，而tomcat的环境是JDK1.7版本，只需要修改tomcat环境的JDK就可以了


| JDK版本 |序号 |
| --- | --- |
| Java SE 10 | 54 (0x36 hex)  |
| Java SE 9 | 53 (0x35 hex)  |
| Java SE 8 | 52 (0x33 hex)  |
| Java SE 7 | 51 (0x33 hex)  |

### 解决方案
- Linux服务器修改tomcat的jdk版本
    - 暂停tomcat
    - 修改catalina.sh和setclasspath.sh,在上面的两个shell脚本开头的地方指定JAVA_HOME 
```
export JAVA_HOME=/opt/hermes/jdk1.8.0_111
```


### 总结
- 这个问题我刚开始以为是dubbo的原因，因为PaymentHubService是通过dubbo进行注册的。从而没有看错误提示，就多花费了一些无用功。根据这个异常UnsupportedClassVersionError其实就可以判断出什么原因了。
