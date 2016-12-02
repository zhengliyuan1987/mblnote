---

title: mysql 命令
date: 2016-11-09 15:13:48
tags: [技术学习,数据库,mysql,sql]
categories: 技术学习
keywords: 技术学习,数据库,mysql,sql
description: 介绍mysql的sql语句

---

# mysql 语句

## 返回players表中town列所有数据项打集合以','分割的集合
SELECT group_concat(town) FROM `players` group by town

## 获取符合条件的记录个数，表头为count
select count(*) as count from t_cluster_config_xml where cluster_name = 'alto'

## 如果存在则不插入
insert into t_cluster_config_xml(a,b)
select a,b from DUAL WHERE NOT EXISTS(SELECT a FROM t_cluster_config_xml WHERE a = 'a');