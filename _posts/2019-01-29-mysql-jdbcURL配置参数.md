---
layout: post
title:  "mysql jdbcURL参数全解"
categories: mysql
tags:  mysql
author: lijd
---

* content
{:toc}

#### Mysql jdbcURL配置参数

| 参数   |      描述      |
|----------|:-------------:|
| user |  数据库用户名（用于连接数据库） |
| passWord  |    用户密码（用于连接数据库）   |
| useUnicode | 是否使用Unicode字符集，如果参数characterEncoding设置为gb2312或gbk，本参数值必须设置为true |
| characterEncoding | 当useUnicode设置为true，给定编码，常用utf8，默认是：autodetect |
| autoReconnect | 当数据库连接异常中断时，是否自动重新连接 |
| autoReconnectForPools | 是否使用针对数据库连接池的重连策略 |
| maxReconnects | autoReconnect设置为true时，重试连接的次数 |
| failOverReadOnly | 自动重连成功后，连接是否设置为只读 |
| zeroDateTimeBehavior | "exception", "round" and "convertToNull"，默认exception |
| maxRows | 返回的最大行数，默认-1，不限制 |
| autoDeserialize |  driver自动发现，并行化存储blob字段 |
| allowMultiQueries | 允许一个statement执行多个用;分割的sql，默认false |
| useSSL | 连接MySQL 5.5.45+, 5.6.26+ or 5.7.6+默认为true，之前低版本为false |

参考：[MySql jdbcURL参数全解](https://blog.csdn.net/mar_ljh/article/details/80981710)
