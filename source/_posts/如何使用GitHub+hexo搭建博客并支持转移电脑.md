---
title: 如何使用GitHub+hexo搭建博客并支持转移电脑
date: 2020/7/23 10:01:23
tag:  实用
---

## 安装准备

### 软件

在搭建hexo博客前，需要下载以下软件（也不算软件吧）：

[Node.js](https://nodejs.org/en/)

[Git](https://nodejs.org/en/)

[Sublime](https://nodejs.org/en/)(其实这个可下可不下，只是怕直接文本修改时编码不对，会导致错误)

**安装没有特别规定，直接next，然后install就好了**

### 账号

一个 [github](http://github.com/)（GitHub官网速度较慢，别急）

<!--more-->

------

## 搭建

**粗体处都是坑点，仔细看**

### 1、配置本地电脑的SSH到Github

first，进入Git的安装位置，找到git-bash.exe并打开

<img src="C:\Users\lenovo\Desktop\3.png" alt="3" style="zoom: 67%;" />

忘记了Git安装位置的小伙伴们可以从开始菜单栏找

<img src="C:\Users\lenovo\Desktop\1.png" alt="1" style="zoom:;" />![2](C:\Users\lenovo\Desktop\2.png)

~~其实在菜单栏找到Git Bush后，直接双击就可以打开git-bash.exe了~~

打开了后输入：

```
ssh-keygen -t rsa -C "这里填GitHub网站注册的邮箱"
```

然后4下回车，就会出现以下图片,可能有会和这个有点不一样（差不多就行了）

![4](C:\Users\lenovo\Desktop\4.png)

之后，就打开GitHub官网，登录账号，然后点击头像再点击setting

![5](C:\Users\lenovo\Desktop\5.png)

你会在这个页面的左边发现这个，点击它

![6](C:\Users\lenovo\Desktop\6.png)

进入页面后点击右上角的绿色按钮  *New SHH key*

![7](C:\Users\lenovo\Desktop\7.png)

这时会让你填Title和Key，Title乱填什么都可以，Key要打入我们刚刚生成的钥匙，钥匙的位置在 `C:\Users\你的用户名\.ssh`，打开文件夹后，你会发现一个叫`id_rsa.pub`的文件，右键记事本打开，把里面的东西都复制到GitHub的Key框那里![8](C:\Users\lenovo\Desktop\8.png)

## 2、本地运行Hexo

### 安装Hexo

首先，你需要一个储存博客的空文件夹，在哪里创建都可以。本文空文件夹创建在`F:`

名字叫做`blog`，位置是`F:/blog`  **避免使用中文或者中间带空格的名字，有可能会出问题**

进入[Hexo官网](http://hexo.io/)，你会发现中间有一串乱七八糟的代码，这就是Hexo的安装代码

这时，我们要打开`cmd` （win+r建，输入cmd），然后（敲黑板，重点来了），你要将cmd输入那一行的前面一串的位置调到刚刚创的文件夹上（不会表达请见谅）

如何调：

#### （1）打盘，例如：`F:`（因为我的文件夹设置在F盘，固这里打F:，**请不要直抄，按实际情况填写**）

![9](C:\Users\lenovo\Desktop\9.png)

#### （2）运用cmd的cd命令调位置 ，例如：`cd blog`因为我的文件夹在F盘的根目录，固只用cd一次即可

![10](C:\Users\lenovo\Desktop\10.png)

**如果各位的位置不是在根目录，cd多几次即可，如下图**

![11](C:\Users\lenovo\Desktop\11.png)

#### （3）然后打入给出的那行命令：`npm install hexo-cli -g`，等待安装即可



**记住先别关`cmd`！如果关了请重新cd到文件夹的位置**



### 创博客

我们在原来的cmd上输入：`hexo init 博客名`，博客名打什么都可以

这时，需要时间。安装完成后，可能会有一些写着`WARN`的黄色的东东，这时正常现象


