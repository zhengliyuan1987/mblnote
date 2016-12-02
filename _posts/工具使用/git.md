---

title: git
date: 2016-11-09 15:13:48
tags: [工具使用,git]
categories: 工具使用
keywords: 工具使用,git
description: 记录git的常用命令。

---

## git push origin master报错

fatal: could not read Username for 'https://github.com': No such file or directo
原因使用https方式的时候 在git remote add origin 的https url 里面没有用户名和密码
修改为如下：
git remote add origin https://{username}:{password}@github.com/{username}/project.git
https://github.com/kemayo/sublime-text-git/issues/176
或者直接修改 .git/config 隐藏文件 为git remote add origin https://{username}:{password}@github.com/{username}/project.git 格式




## 显示当前分支

git branch

## 显示远程信息

git remote -v


## 强制回退到master分支

取回远程主机某个分支的更新，再与本地的指定分支合并
git pull <远程主机名> <远程分支名>:<本地分支名>
git pull origin master:master -f

## 显示git状态

git status

git branch * master


## 将master分支合并到当前分支

git merge master



## 将远程master的修改合并到本地mbl分支。

git pull origin master:master -f
git add .
 git commit -m "test"
git pull origin master:master -f
git branch * master
git checkout mbl
git pull
git merge master
 git push



## 取消commit 和 pull

git reset --hard <commit_id>
git push origin HEAD --force


## git 更换仓库
1. 从原地址克隆一份裸版本库，比如原本托管于 GitHub
git clone --bare git://github.com/username/project.git
2. 然后到新的 Git 服务器上创建一个新项目，比如 GitCafe。
3. 以镜像推送的方式上传代码到 GitCafe 服务器上。
```
cd project.git
git push --mirror git@gitcafe.com/username/newproject.git
```
4. 先查看remote的名字
```
git branch -r
```
5. 假设你的remote是origin，用git remote set_url 更换地址
```
git remote set-url origin remote_git_address
```


## 提交代码
```
git commit -am "提交说明"
```