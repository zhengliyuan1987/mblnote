---
title: alluxio介绍与安装
date: 2016-12-13 09:23:00
tags: [技术学习,bigdata]
categories: 技术学习
keywords: 技术学习,bigdata,alluxio
description: alluxio介绍与安装

---

## 介绍
- 概念：是一个开源的基于内存的分布式存储系统，现在成为开源社区中成长最快的大数据开源项目之一。

## 公司简介

- 由项目的创建者李浩源以及来自UC Berkeley, Google, CMU, Palantir, Stanford, Yahoo等不同公司和学校的项目核心开发者组成。
- 完成750万 dollars 的A轮融资，由Andreessen Horowitz投资（硅谷最著名的VC之一，主要成员为网景公司创始人之一）。

作者：Mingche Su
链接：https://zhuanlan.zhihu.com/p/20624086
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

## 术语
- Amazon AWS ：亚马逊AWS 云服务-中国领先的可扩展云计算平台
- Amazon S3 ：是一种在Internet 上的云存储服务。 要上传数据（照片、视频、文档等），请首先在一个AWS 区域中创建存储桶。 然后，您可以将任何数量的对象上传到该存储桶。


## 安装
- 解压
```bash
$ tar -xzf alluxio-1.3.0-bin.tar.gz
$ cd alluxio-1.3.0
```
- 生成配置文件
```bash
./bin/alluxio bootstrapConf localhost
```

## 格式化Alluxio
我们格式化Alluxio为启动Alluxio做准备。如下命令会格式化Alluxio的日志和worker存储目录，以便接下来启动master和worker。
```bash
./bin/alluxio format
```
## 启动 
我们启动Alluxio！Alluxio默认配置成在localhost启动master和worker。我们可以用如下命令在localhost启动Alluxio：
```bash
./bin/alluxio-start.sh local
```
恭喜！Alluxio已经启动并运行了！你可以访问http://localhost:19999查看Alluxio master的运行状态，访问http://localhost:30000查看Alluxio worker的运行状态。

## 使用Alluxio Shell
- 列出文件
```bash
./bin/alluxio fs ls /
```
- 上传文件
```bash
./bin/alluxio fs copyFromLocal LICENSE /LICENSE
```
- 查看文件
```bash
./bin/alluxio fs cat /LICENSE
```

## 关闭
```bash
./bin/alluxio-stop.sh all
```