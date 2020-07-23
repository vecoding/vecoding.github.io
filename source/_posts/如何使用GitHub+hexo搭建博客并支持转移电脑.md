---
title: 如何使用GitHub+hexo搭建博客并支持转移电脑
date: 2020/7/23 10:01:23
tag: 实用
---

# 安装准备

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

# 搭建

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

### 2、初步部署博客

#### 安装Hexo

首先，你需要一个储存博客的空文件夹，在哪里创建都可以。本文空文件夹创建在`F:`

名字叫做`blog`，位置是`F:/blog`  **避免使用中文或者中间带空格的名字，有可能会出问题**

进入[Hexo官网](http://hexo.io/)，你会发现中间有一串乱七八糟的代码，这就是Hexo的安装代码

这时，我们要打开`cmd` （win+r建，输入cmd），然后（敲黑板，重点来了），你要将cmd输入那一行的前面一串的位置调到刚刚创的文件夹上（不会表达请见谅）

如何调：

##### （1）输入盘，例如：`F:`（因为我的文件夹设置在F盘，固这里打F:，**请不要直抄，按实际情况填写**）

![9](C:\Users\lenovo\Desktop\9.png)

##### （2）运用cmd的cd命令调位置 ，例如：`cd blog`因为我的文件夹在F盘的根目录，固只用cd一次即可

![10](C:\Users\lenovo\Desktop\10.png)

**如果各位的位置不是在根目录，cd多几次即可，如下图**

![11](C:\Users\lenovo\Desktop\11.png)

##### （3）用`npm config set registry https://registry.npm.taobao.org`**切换npm的下载源**，然后再打入给出的那行命令：`npm install hexo-cli -g`，等待安装即可

之前我就被这里坑到。原本是可以不切换下载源的，但是npm下载源在国外，那速度简直了，不切换国内下载源很可能中途来个安装失败。**如何看是否是安装失败：你看看安装完后前面的一串英文是否有error的字眼（无需区分大小写）或者ERR**



**记住先别关`cmd`！如果关了请重新cd到文件夹的位置**

------

### 5、搭建博客

我们在原来的cmd上输入：`hexo init 博客名`，博客名打什么都可以

这时，需要时间。安装时，可能会有一些写着`WARN`的黄色的东东，这是正常现象。安装完后，你之前建的文件夹内就出现了名字为刚刚你打的博客名的文件夹，**这是正常现象**



重点又来了

首先**我们要cd到这个文件夹内**，然后输入`npm install`进行安装

**再次提醒，记得切换下载源！！不切换国内下载源很可能中途来个安装失败。**

这时，我们基本已经创好博客了，你可以在cmd输入`hexo s -p 端口 `，然后它会给出一个网址供查看自己的博客。如果你在cmd输入Ctrl+C即可停止这个端口



**cmd别关！**

------

# 将博客上传到GitHub供大家浏览

进入GitHub，点击右上角的+号，点击`New repository` 新建一个仓库，Repository name处**必须**填`你的的Github用户名.github.io`，**如果`.github.io`前不是填你的GitHub用户名，查看博客时只会显示`undefined`**。还有一些细节需要注意的是，**要保证下面的选项选的是`Public`，并且`Initialize this repository with a README`处要打上钩**

然后点击`Create repository`创建仓库

我们现在就到了仓库的页面，点击右侧的`Code`并把那个链接复制下载

然后我们用Sublime打开我们刚刚自动创建的以你打的博客名为名字的文件夹，打开`_config.yml`，拉到最下面，在`type:`处输入git

然后我们在`type:`下一行输入`repo:`，然后粘贴刚刚复制的地址

之后我们就在`repo:`后加上一行，输入`branch: master`

接着我们往上拉，找到`url:`后面输入：`http://你的Github用户名.github.io`

上方还有一个author，改成你想要的名字，表示这个博客是谁的

**冒号后记得留一个空格，如果前面的type没有变红就表示没留空格**

**记得检查，避免错误**

最后点击Sublime内的关闭（注意不是整个程序的叉）

之后，我们回到cmd（记得退本地端口），输入 `npm install hexo-deployer-git --save`，安装Git插件。

安装完后我们在 `cmd` 中输入`hexo g`，代表本地文件生成，回车后输入 `hexo d`，代表上传。

这次的hexo d一**定会是失败的**，你会发现后半部分**有Error:Spawn failed（如果不是这个请百度）**，就说明我们此时还有配置Github账号才能正常上传。你要输入两行代码，这两行代码在刚刚失败的报告中有显示，也就是让你配置Github账号，那两串代码如下：

```
git config --global user.email "你的邮箱"
git config --global user.name "你的用户名"
```

**引号别丢了**

再次`hexo d` 后它会让你输入邮箱和密码，输密码的时候他是不会显示的，不要以为看不到就是没输入到。上传完毕后，**如果有Error:Spawn failed，这证明你账号或密码打错了**，重新尝试即可。成功后，你就可以开始你的博客之旅了！网址就是：`你的用户名.github.io`



**这里一直叫大家用cmd做这些操作而不是用git-push.exe，是因为cmd有颜色显示，警告和错误的地方有黄色和红色显示，比较容易发现问题**

------

# 上传博客文章

我们进入 `博客名\source\_posts`，这里就是放博客的地方。如果要写博客，最好使用一些 Markdown+LaTeX编辑器，比如Typora

博文的后缀**必须为'.md'**，我们可以新建一个txt文件然后改后缀即可（记得关掉隐藏扩展名）

之后我们在最上面加上这样一段：

```
---
title: 文章的标题
date: 发布时间
tag: 标签
---
```

**一样的规矩，记得冒号后留空格！！**

如果我们写好了一篇文章，我们还需要上传，这时我们要打开 `cmd`，`cd` 到你的博客的位置，然后输入这三行代码：

```
hexo clean
hexo g
hexo d
```

**同样的，如果有Error:Spawn failed，这证明你账号或密码打错了。**

成功后，**等待一段时间**后再回到博客，就可以看到更新了。

------

# 主页文章显示过多：

正常时，上传博客后往往会在首页将整篇文章的内容都显示出来，如果你觉得不好看，可以在本地`.md`文章中加入一行代码：`<!--more-->`，然后重新上传，这样它后面的内容就不会显示出来了，而是改成Read More按键

------

# 本地博客的转移

很多时候，我们都需要跑来跑去，自己的电脑不在身边，无法写博客怎么办？这时个非常苦恼的问题，这里讲述如何使用GitHub的分支功能储存博客的源文件，实现随处写博客。