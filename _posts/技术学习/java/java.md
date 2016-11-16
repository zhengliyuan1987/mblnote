---
title: java 远程调试
date: 2016-11-09 15:13:48
tags: [技术学习,java]
categories: 技术学习
keywords: 技术学习,java,远程调试
description: 介绍java远程调试
---
## 远程调试
```
java -Xdebug -Xnoagent -Djava.compiler=NONE -Xrunjdwp:transport=dt_socket,server=y,suspend=y,address=2345 Main
```