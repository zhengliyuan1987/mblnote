---
title: linux命令
date: 2016-11-09 15:13:48
tags: [技术学习,linux,centos]
categories: 技术学习
keywords: 技术学习,linux
description: 介绍linux软件安装，配置
---
#linux 常用命令

	* history |grep scp
	* tail -f log/UGDAP.log
	* 只显示文件名：
ls -l | grep ^[^d] | awk '{print $8}'
只显示文件夹名：
ls -l |grep ^d | awk '{print $8}' 或者是 ls -d */


## 恢复rm删除的文件 ##

### 显示所删除的文件所在的分区 ###
df -T /home

### 用debugFS查找被删除文件的inode号 ###
sudo debugfs
debugfs>open /dev/sda5
debugfs>ls -d /home/mbl/study
尖括号中的是inode

### 恢复inode ###
extundelete ${dev_describer} --restore-inode ${inode} 


### 如果知道被删除文件的完整的路径，直接恢复 ###
extundelete ${deb_describer} --restore-file ${path}  


## 	shell脚本常用变量 ##

$0: shell或shell脚本的名字
$*:以一对双引号给出参数列表
$@:将各个参数分别加双引号返回
$#:参数的个数
$_:代表上一个命令的最后一个参数
$$:代表所在命令的PID
$!:代表最后执行的后台命令的PID
$?:代表上一个命令执行后的退出状态


## curl ##


 curl -x 172.22.91.78:80 http://172.16.172.95:19888/ws/v1/history/mapreduce/jobs/job_1470405196301_64273|python -m json.tool>job_1470405196301_64273.json


## 显示当前版本 ##

cat /proc/version
uname -a
cat /etc/*release*

## 显示ip ##

hostname -i
ifconfig -a|grep inet|grep -v 127.0.0.1|grep -v inet6 | awk '{print $2}' | tr -d "addr:"
ifconfig enp0s25|grep inet|grep -v 127.0.0.1|grep -v inet6 | awk '{print $2}' | tr -d "addr:"


## 测试端口是否通 ##

telnet 172.22.91.34 8087


## 查看端口是否被占用 ##

netstat -tunlp |grep 80
lsof -i 80

/bin/bash^M: 解释器错误: 没有那个文件或目录
sed -i 's/\r$//' check_tool.sh

## 后台启动进程，重定向输出到文件 ##

nohup command > myout.file 2>&1 &

## 杀进程 ##

ps -ef | grep tomcat | awk '{print $2}' | xargs kill -9
或
kill `ps -ef | grep [j]enkins.war | awk '{ print $2 }'`
虽然提示没有找到进程pid，但已经杀掉了


## 开机自动挂载分区 ##

用blkid列出分区uuid和type
sudo  blkid
接下来修改自动挂载的配置文件： 
sudo vim /etc/fstab
增加一行
UUID=11263962-9715-473f-9421-0b604e895aaa /data       ext4    defaults 0     1



## zip解压中文乱码 ##

ubuntu下  unzip -O CP936  xxx.zip -d exdir

## 权限 ##
home目录不能有其它用户写权限
/root  

.ssh 只能是 700

linux权限
777 rwxrwxrwx  （所有者，本组用户，其它用户）rwx=读，写，执行


## ssh-copy-id ##

## 设置root密码 ##
sudo passwd root




## 在任务栏显示网速 ##
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install indicator-netspeed

## 设置显示桌面快捷键 ##


sudo apt-get install compizconfig-settings-manager
ccsm

## KWPlayer 酷我音乐盒  ##

## Iptux — 局域网聊天工具(飞鸽Linux版) ##
sudo apt-get install iptux

## System Load Indicator ( 系统状态指示器） ##

sudo add-apt-repository ppa:indicator-multiload/stable-daily
sudo apt-get update
sudo apt-get install indicator-multiload

## XBMC（媒体中心） ##
XBMC（媒体中心）
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get install xbmc

## VMware Workstation ##
安装方法（包含下载、安装、激活、序列号）
http://www.kashu.org/1024.html



## wireshark ##
http://ppa.launchpad.net/wireshark-dev/stable/ubuntu/pool/main/w/wireshark/
ppa:wireshark-dev/stable









.tar.gz     格式解压为          tar   -zxvf   xx.tar.gz
.tar.bz2   格式解压为          tar   -jxvf    xx.tar.bz2


## 查看linux版本 ##
rpm -qa|grep kernel

中文Linux 常用的locale是zh_CN.gb2312，zh_CN.gbk，zh_CN.gb18030 和 zh_CN.UTF-8 。通过如下命令可以查询系统的locale：#echo $LANG

fdisk -l 

mkdir /mnt/usb
mount命令格式：mount [-参数] [设备名称] [挂载点] [其他参数]
mount /dev/sdb1 /mnt/usb
umount /dev/sdb1