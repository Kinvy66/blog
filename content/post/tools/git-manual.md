---
title: "Git的基本命令"
description: "版本控制软件Git的基本使用和命令"
date: 2022-04-28T11:15:00+08:00
image: https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/20220428th_id=OHR.GreatRidge_ZH-CN6165605288.jpg
math: 
hidden: false
comments: true
draft: true
categories: ["Tools"]
tags: ["Git", "GitHub"]
lastmod:
---



##  一、Git的安装



1. 下载Git 

   官网 ：[Git (git-scm.com)](https://git-scm.com/) 提供多种版本下载， 根据需要下载， 这里以  64位安装版为例

   ![image-20220428112258463](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20220428112258463.png)

2. 安装

   安装过程中需要选择的项比较多，但是如果没有特别要求，基本所有的都保持默认设置，一直Netx，直到安装完成。安装完成后右键菜单会有下面这两个选项

   ![image-20220428144816802](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20220428144816802.png)



## 二、基本配置

Git安装后基本不需要配置，只要配置一下邮箱和用户名就可以了

右键打开 GitBash

配置全局的用户名

```shell
$ git config --global user.name 'name'      #将name替换为自定义的用户名
```

配置全局的用户名

```shell
$ git config --global user.email 'email'  #将email换成邮箱地址
```

 查看当前的所有配置项

```shell
$ git config --list #查看配置信息
```



## 三、Git的基本使用

创建一个文件夹作为仓库的根目录，这里以 `Rep` 文件夹为例，在 `\Rep` 的根目录下打开GitBash

1. 创建仓库, 初始当前文件夹 `\Rep` 为Git仓库

   ```shell
   $ git init  
   ```

   ![image-20220428150119876](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20220428150119876.png)

   创建完成后，当前文件夹被识别为一个Git仓库，在文件路径的后面显示当前所在的分支名称 `master`



2. 查看当前仓库的文件状态

   ```shell
   $ git stauts
   ```

   ![image-20220428150635274](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20220428150635274.png)

   新建的仓库没有任何文件的修改

3. 暂存修改的文件

   添加一个 `README.md` 文件， 使用 `git status` 查看文件状态

   ![image-20220428150949626](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20220428150949626.png)

   将文件添加到暂存库

   ```shell
   $ git add [文件名]  # git add . 将所有修改的文件添加到暂存库
   ```

   如果需要将多个文件添加到暂存库，文件名之间用空格隔开，一般情况下都是使用 `git add .` 命令将所有的修改的文件添加到暂存库



4. 提交暂存的文件

   ```shell
   $ git commit -m '提交的信息'  
   ```

   提交信息是本次修改的内容的简单描述，比如新建了一个 README 文件， 那可以写 `添加README` 。 这个描述信息没有固定的，可以按自己的需要写



5. 查看提交历史

   ```shell
   $ git log
   $ git log -n    #查看最近n条的日志
   $ git log --pretty=oneline    #一行简略的显示日志
   ```



6. 修改上一次的提交信息

   本地仓库如果提交了，但是提交时写的描述不太准确，需要修改，可以使用下面的命令，这个只对最近一次的提交修改

   ```shell
   $ git commit --amend -m '修改的内容'
   ```



7. 丢弃修改

   丢弃没有add进暂存区的修改

   ```shell
   $ git checkout -- 文件名  # 丢弃指定文件的修改
   $ git checkout . #本地所有修改的。没有的提交的，都返回到原来的状态
   ```

   

## 四、远程相关命令

常用的Git远程仓库有 GitHub, GitLab, Gitee, 下面以GitHub为例

### 1. 本地仓库关联远程仓库

 将本地的参考推送到远程的仓库并关联，首先需要在GitHub新建一个仓库

1. 本地仓库关联远程仓库

   ```shell
   $ git remote add origin 远程仓库的链接
   # 例如
   $ git remote add origin https://github.com/Kinvy66/Rep.git
   ```

2. 推送本地仓库，推送之前本地需要将所有的修改文件 `commit`

   ```shell
   # 推送命令
   $ git push -u origin master     #将本地的推送到远程，同时本地的master和远程的关联 
   $ git push -f -u origin master  # 强制提交
   # 简写
   $ git push
   ```

   第一个命令是指定远程仓库名和分支名，这两个命令在只有一个分支的情况下是一样的，但是当仓库有多个分支的时候使用简写形式是无法推送的。

3. 拉取远程仓库，拉取之前同样需要将所有的修改文件 `commit`

   ```shell
   # 推送命令
   $ git pull  origin master     #拉取远程仓库的master分支
   # 简写
   $ git pull
   ```

   和推送命令一样，在只有一个分支的情况下这两个命令是一样的，如果是多分枝就必须使用第一个命令



4. 其他远程操作命令

   ```shell
   $ git remote show    #列出远程仓库的别名
   $ git remote show   origin #列出origin的详细信息
   ```

   



### 2. 克隆仓库

上面的拉取和推送都基于本地和远程仓库建立了关联的前提下的操作。克隆的使用场景就是我们下载别人开源的仓库

```shell
$ git clone  远程仓库地址
# 例如
$ git clone https://github.com/Alinshans/MyTinySTL.git
```





## 五、Git分支

Git仓库初始化的时候默认会创建一个 `master` 分支

1. 查看当前仓库分支

   ```shell
   $ git brach    #查看当前所有的分支
   ```

2. 新建分支

   ```shell
   $ git branch new_branch    	  #创建新的分支（new_branch）
   $ git checkout -b new_branch  #创建并切换到new_branc分支
   ```

3. 切换分支

   ```shell
   $ git checkout new_branch   #切换到new_branc分支
   $ git checkout -            #切换到之前的分支
   ```

4. 更改分支名称

   ```shell
   $ git branc -m old_branch new_branch  #更改分支的名字
   ```

5. 删除分支

   ```shell
   $ git branch -d new_branch    #删除new_branch分支，没有合并分支无法删除
                               #使用下面的命令可以强制删除
   $ git branch -D new_branch
   ```

6. 合并分支

   ```shell
   $ git merge new_branch  #将new_branch分支的修改内容合并到当前所在的分支
   ```

7. 拉起本地不存的远程分支并创建一个本地分支

   ```shell
   $ git checkout -b 本地分支名 origin/远程分支名
   ```

8. 其他

   ```shell
   $ git branch -v    #查看当前分支最近一次提交的信息
   ```

   

## 六、版本回退

**方法一：git reset**

1. 查看提交历史，确定回退版本

   ```
    git log
   ```

2. 回退到某个版本

   ```
    git reset --hard [版本号，只需前几个字符就可以]
   ```

3. 强制提交到远程

   ```
    git push -f -u origin master
   ```

注意：回退之后强制提交到远程，回退版本之后的提交历史会没有的。

**方法二：git revert**

git revert 撤销 某次操作，此次操作之前和之后的commit和history都会保留，并且把这次撤销作为一次最新的提交

```
  git revert HEAD                #撤销前一次 commit
  git revert HEAD^               #撤销前前一次 commit
  git revert commit （比如：fa042ce57ebbe5bb9c8db709f719cec2c58ee7ff）#撤销指定的版本，撤销也会作为一次提交进行保存。
```

`git revert`是提交一个新的版本，将需要revert的版本的内容再反向修改回去，版本会递增，不影响之前提交的内容



## 七、其他

### 1. 生成SSH密钥

1. 查看是否有密钥：

   ```shell
    $ cd ~/.ssh        #没有的话，不会有这个文件
   ```

2. 生成密钥

   ```shell
   $ ssh-keygen -t rsa
   ```

3. 最后得到了两个文件：id_rsa和id_rsa.pub

   ```shell
    $ cat ~/.ssh/id_rsa.pub
   ```

   将这个文件内容复制到GitHub



## 附录

更多Git操作和命令查阅官方文档： [Git - Documentation (git-scm.com)](https://git-scm.com/doc)









