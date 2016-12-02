---
title: maven
date: 2016-11-16 15:13:48
tags: [工具使用,maven]
categories: 工具使用
keywords: 工具使用,maven
description: 记录maven的常用命令。
---

## maven 安装本地库
mvn install:install-file -DgroupId=com.facebook.presto -DartifactId=presto-jdbc -Dversion=0.132-SNAPSHOT -Dpackaging=jar -Dfile=presto-jdbc-0.132-SNAPSHOT.jar