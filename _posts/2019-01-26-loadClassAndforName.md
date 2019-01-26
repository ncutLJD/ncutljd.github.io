---
layout: post
title:  "loadClass和forName的区别"
categories: JVM
tags:  Java JVM
author: lijd
---

* content
{:toc}

#### 类的加载方式

* 隐式加载：new
* 显式加载：loadClass，forName等

#### loadClass和forName的区别

##### 类的装载过程

如下图所示，类的加载过程分为三步
- 加载、链接和初始化

![image](http://129.204.42.126/images/%E7%B1%BB%E7%9A%84%E8%A3%85%E8%BD%BD%E8%BF%87%E7%A8%8B.png)

##### loadClass和forName

- loadClass 链接默认是false
```
public Class<?> loadClass(String name) throws ClassNotFoundException {  
    //resolve 默认是false 所以不会链接指定的类
    return loadClass(name, false);
}

protected Class<?> loadClass(String name, boolean resolve)   throws ClassNotFoundException{
    ......

    if (resolve) {    resolveClass(c); }
    ......
}

//Links the specified class.
protected final void resolveClass(Class<?> c) {  resolveClass0(c); }

```


- forName 默认是初始化的
```
public static Class<?> forName(String className)  throws ClassNotFoundException { 
    // initialize true
    return forName0(className, true,                                                                ClassLoader.getClassLoader(Reflection.getCallerClass()));
 }

```
##### 有forName为什么还需要loadClass？

这是在不同的场景有不同的作用
forName可以初始化静态块
例如mysql的Driver驱动 就是通过forName进行加载的
```
Class.forName("com.mysql.jdbc.Driver");

public class Driver extends NonRegisteringDriver implements java.sql.Driver {   
    public Driver() throws SQLException {    }   
    static {       
        try {           
            DriverManager.registerDriver(new Driver());       
        } catch (SQLException var1) {
            throw new RuntimeException("Can't register driver!");       
       }   
    }
}
```

Spring ioc为了加快初始化速度，因此大量使用了延时加载技术。而使用classloader不需要执行类的初始化代码，可以加快加载速度，把类的初始化工作留到实际使用到这个类的时候。
