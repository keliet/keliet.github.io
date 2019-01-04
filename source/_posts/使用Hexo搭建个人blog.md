---
title: 使用Hexo搭建个人blog
categories: Other
tags:
  - Hexo
  - Github
date: 2016-12-15
---
![](https://blog-images-1258448410.cos.ap-chengdu.myqcloud.com/blog-images/Hexo_title.png)

<!--more-->
# 搭建过程
在开始之前，简单说明一下整个博客的一个搭建过程：
-  **本地部署**
-  **远程部署**
-  **图片存储**
-  **写文章**
-  **发布**
-----------------------

# 本地部署
## 安装相关软件
安装[Git](https://git-scm.com/)和[Node.js](https://nodejs.org/)
安装过程一路默认，需要的话可更改安装目录
## 安装Hexo
Hexo的安装需要借助Node.js的`npm`命令，可以理解为Hexo是Node.js的模块。操作的方式是在任意的位置单击鼠标右键，选择Git bash命令，或者直接点击Git Shell快捷方式，在里面输入：
```
npm install  -g  hexo
```
其中`-g`代表使用全局安装；卸载的话，将上面的命令中的`intall`更换为`uninstall`就可以了。
## 初始化Hexo
在某个盘符下创建一个目录，重命名（最好是英文），例如你在D盘中创建了一个blog目录，那么路径就是D:\blog，后续的很多操作都会在这个目录中；在该目录单击右键，选择`Git bash`，输入以下命令：
```
hexo init
```
成功后，会在选中目录中自动生成如下结构

![](https://blog-images-1258448410.cos.ap-chengdu.myqcloud.com/blog-images/hexo_1.png)
**安装依赖包**
```
 npm install
```
成功后，会在选中目录中自动生成`node_modules`目录；一系列的安装后，本地博客就搭建完毕了，输入如下的命令（也可以利用组合命令）先输入`hexo g`再输入`hexo s`
```
D:\blog> hexo g
INFO  Start processing
INFO  Files loaded in 558 ms
INFO  Generated:
\\省略部分结果
```
使用`hexo g`，不出意外，会在blog目录中生成public目录和db.json文件，其中public就是我们博客的静态页面，远程部署的时候就是将该目录中的所有文件上传至服务器。
```
D:\blog> hexo s
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.
```
组合命令：`hexo s -g`
```
D:\blog> hexo s -g
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.
```
在浏览器中地址栏输入`localhost:4000`就可以看到本地部署的效果了，就如下图的样子，这里的是本地博客，其他地方还看不到的；
![](https://blog-images-1258448410.cos.ap-chengdu.myqcloud.com/blog-images/hexo_2.png)
## 安装Hexo主题
使用Hexo更换主题还算方便，先使用克隆命令安装好主题，然后更改一下博客的配置文件D:\blog\_config.yml里面的主题名称就好了。关于主题的选择，每个人的喜好不同，你可以到[Hexo官方主题](https://hexo.io/themes/)页面选择自己喜欢的主题。我选用的是经过自己修改的NexT主题。后面都是针对于NexT主题的介绍。说明一点：使用他人的主题，一定要保留主题作者的信息（在博客最下面显示），表示对作者的尊重。
遇到喜欢的主题后，找到主题的github链接；在blog目录下右键单击选择`Git Bash`，输入以下命令：
```
git clone https://github.com/iissnan/hexo-theme-next.git themes/next
```
在blog目录的themes文件夹下会找到获得的主题文件夹`next`；之后在blog目录下的_config.yml文件中找到如下字段：
``` python
## Themes: https://hexo.io/themes/
theme: landscape   #将该字段更改我们新获取的主题文件夹名就好
```
我这里是使用的next主题，就将该字段更改为next
## 博客配置
博客搭建完毕，就可以根据自己的爱好对Hexo生成的网站进行设置了，对整站的设置置分为整体配置和主题配置。
先来看看博客的**整体配置**，也就是打开blog目录中的`_config.yml`文件，更改里面的部分内容。
```python
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site
title:                       #填写网站名，会在标签页上显示
subtitle:                    #网站副标题
description:                 #网站描述，便于搜索引擎用关键词检索
author:                      #作者
language: zh-Hans            #语言，具体配置与使用主题有关，查看主题文档

#URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://yoursite.com
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:

# Directory
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing
new_post_name: :title.md # File name of new posts
default_layout: post #l post  、draft、page         #文章、草稿、页面
titlecase: true # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace:

# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss

# Pagination
## Set per_page to 0 to disable pagination
per_page: 12               #每页显示12篇文章
pagination_dir: page
archive: 1
category: 1
tag: 1
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: landscape
fancybox: true
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:                      #github相关配置，主要用于，将生成网站上传至github
 type: git
 repo: https://github.com/keliet/keliet.github.io.git
 branch: master

```
有关详细说明请查阅[Hexo文档](https://hexo.io/zh-cn/docs/index.html)其中有更详细的说明；整体配置设置完以后 。
再来看看**主题配置**，在主题文件夹下找到`_config.yml`文件；其中各个字段的说明，请查看next主题的[说明文档](http://theme-next.iissnan.com/getting-started.html)，已经说的非常清楚了。
# Hexo 常用命令说明
# 远程部署
-----------------------
远程部署流程，简单说明一下整个过程：
-  **创建仓库**
-  **创建分支**
-  **拷贝仓库**
-  **部署要上传hexo配置**
-  **提交网站相关文件**
-  **生成网站并发布到github上**
-  **日常使用**
-----------------------
## 创建仓库
远程部署可部署到自己的服务器上，也可以托管到Github上，这里我只说一下Github方式。因为是托管到Github上，所以第一步需要注册一个账号。已有账号的自行忽略。

**第一步：**建立和用户名相对应的仓库，以我的例子来说，我的用户名是keliet,那么我的仓库就必须是keliet.github.io，否则可能就不成功。

**第二步：**远程代码是基于SSH的，所以需要SSH的相关配置。方法是现在本地生成SSH公钥，然后添加到Github上面。具体的操作如下：

**1、检查你电脑上现有的ssh key：**
```
ls ~/. ssh 检查本机的ssh密钥
```
如果提示：No such file or directory 说明没有找到，说明本地没有ssh密钥。

**2、生成新的SSH Key：设置你的邮箱和用户名**
```
git config --global user.email "keliet1021@gmail.com"
git config --global user.name "keliet"
```
接下来生成密钥，过程中会要设置密码，输入的密码不显示（第一次为设置密钥文件名，第二和第三就是密码与密码确认）
```
ssh-keygen -t rsa -C "keliet@gmail.com"
```
注意其中的-C是大写。上述的命令成功后，会得到id_rsa和id_rsa.pub两个文件，可能在`C:\Users\Administrator\.ssh`文件夹里。

**3、把ssh密钥添加至Github上**
登陆Github后，点击settings，然后进入SSH keys，把id_rsa.pub文件里内容添加进去就好了。

**4、配置相关Github信息**
编辑D:\blog目录下的配置文件_config.yml,找到deploy字段，输入以下内容
```
deploy:
  type: git
  repo: https://github.com/你的用户名/你的用户名.github.io.git
  branch: master
```
输入命令`hexo d -g`，完成远程部署；出现下面的提示表示部署成功；
```
INFO Deploy done: git
```
部署过程中遇到问题及解决办法：
```
 create mode 100644 vendors/velocity/velocity.min.js
 create mode 100644 vendors/velocity/velocity.ui.js
 create mode 100644 vendors/velocity/velocity.ui.min.js
replaced by CRLF in vendors/jquery/index.js.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in vendors/velocity/velocity.js.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in vendors/velocity/velocity.min.js.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in vendors/velocity/velocity.ui.js.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in vendors/velocity/velocity.ui.min.js.
The file will have its original line endings in your working directory.
bash: /dev/tty: No such device or address
error: failed to execute prompt script (exit code 1)
fatal: could not read Username for 'https://github.com': No error
FATAL Something's wrong. Maybe you can find the solution here: http://hexo.io/docs/troubleshooting.html
Error: bash: /dev/tty: No such device or address
error: failed to execute prompt script (exit code 1)
fatal: could not read Username for 'https://github.com': No error

    at ChildProcess.<anonymous> (E:\zan\www\gitpages\hexo\zanjs.github.io\node_modules\hexo-deployer-git\node_modules\hexo-util\lib\spawn.js:42:17)
    at emitTwo (events.js:87:13)
    at ChildProcess.emit (events.js:172:7)
    at maybeClose (internal/child_process.js:818:16)
    at Process.ChildProcess._handle.onexit (internal/child_process.js:211:5)

```
**解决办法1：**
配置Deployment首先，你需要为自己配置身份信息，打开命令行，然后输入：
```
git config --global user.name "yourname"
git config --global user.email "youremail"
```
以上做完还不行
删掉blog目录下的文件夹`.deploy_git`，重新deploy就可以了。 

**解决办法2：**
将博客配置`_config.yml`中的deploy:配置为ssh模式，如下所示
```
deploy:
  type: git
  repo: git@github.com:用户名/用户名.github.io.git
  branch: master
```
**解决办法3：**
找到Github快捷方式，进入后登陆账号即可。
此法，配置还是https
```
deploy:
  type: git
  repo: https://github.com/用户名/用户名.github.io.git
  branch: master
```
3种方法适合不同的人，选择自己适用的，如不知道依次试，总有一个可以解决你的问题。

## 创建分支
因为发布后是覆盖方式，即后一次的发布将完全覆盖上次的发布，如果你有多台电脑，而且每台电脑你都有可能会写博客。那么这个时候就需要对Hexo进行版本控制了。版本控制的主要目的是方便在不同的电脑维护Hexo及写作。这里利用github的分支来保存hexo框架的相关文件(hexo配置、md、主题等文件)到github page仓库。

**新建Hexo分支**page仓库的master分支用来存放网站文件的，这是GitHub Page的要求，所以只好新建分支来保存Hexo原始文件，在下图的输入框输入分支名并按回车即完成分支创建。
![](https://blog-images-1258448410.cos.ap-chengdu.myqcloud.com/blog-images/hexo_3.png)
**设置默认分支**因为我们写博客更多的是更新这个分支，网站文件所在的master分支则由hexo d命令发布文章的时候进行发布，所以我们将hexo分支>设置为默认分支，这样我们在新的电脑环境下git clone该仓库时，自动切到hexo分支。按下图进行操作。
![](https://blog-images-1258448410.cos.ap-chengdu.myqcloud.com/blog-images/hexo_4.png)

然后使用部署命令`hexo g -d`就会自动渲染Markdown文件生成静态文件（public文件夹下所有文件）并部署到yourname.github.io仓库的master分支上，这时再访问http://yourname.github.io 就可以看到博客页面了。
## 拷贝仓库
此时博客页面是部署保存了，但hexo配置、md、主题等文件还没有保存，创建新的文件夹，拷贝仓库，用于将hexo的配置发布到hexo分支上。在新创建的目录中执行以下命令：
```
git clone https://github.com/yourname/yourname.github.io.git
```
## 部署要上传hexo配置
在新创建的文件夹中，将本地修改好的hexo配置文件拷贝到新创建的目录；需要拷贝的内容见下图；（以下是必须要拷贝的内容）
![](https://blog-images-1258448410.cos.ap-chengdu.myqcloud.com/blog-images/hexo_5.png)
完成以上的拷贝后就可以提交到hexo分支了。
## 提交网站相关文件
在新创建的目录中执行以下命令：（用于将hexo配置及主题配置提交到github）
```
git add .
git commit -m “你要写的描述”
git push origin hexo
```
## 生成网站并发布到github上
这个就比较简单了，如果配置都按以上操作，只要执行`hexo g -d`后，去刷新你的博客吧。

## 日常使用

**已有环境下**

在本地对博客进行修改（添加新博文、修改样式等等）后，通过下面的流程进行管理。
**1.**同步之前写的博客，在你的仓库目录下执行`git pull`；
**2. **依次执行`git add .`,`git commit -m "..."`、`git push origin hexo`指令将改动推送到GitHub（此时当前分支应为hexo）；
**3.** 然后才执行`hexo g -d`发布网站到master分支上。
虽然后两个过程顺序调转一般不会有问题，不过逻辑上这样的顺序是绝对没问题的（例如突然死机要重装了，悲催....的情况，调转顺序就有问题了）

**新环境**

到了新的电脑上时，我们需要将项目先下载到本地，然后再进行本地部署即可。
```
git clone https://github.com/yourname/yourname.github.io.git
cd yourname.github.io
npm install hexo
npm install
npm install hexo-deployer-git –save
```
之后开始写博客，写好部署好之后，别忘记 `git add .`，`git commit -m "你的描述"`，`git push origin hexo`推上去
# 图片存储
想要在文章中插入图片的话，可以按照Markdown语法来插入，格式`![图片名称](图片地址)`图片的存放有两种方式：
1、在本地`D:\blog\source`目录下新建一个存放图片的文件夹，比如images，然后把想要插入的图片放在里面，插入图片的路径；

2、第二种方法是把图片上传到网络，然后插入图片路径。推荐使用第二种。
本人将图片存在七牛上，在本地任意位置创建图片文件夹，把文章要用的图片存入该文件夹，在七牛开发者中心下载[qrsbox](http://developer.qiniu.com/code/v6/tool/qrsbox.html)，直接运行qrbox，并在其中设置要同步的图片文件夹，图片会自动同步到七牛服务器
# 写文章
文章格式如下：
```markdown
---
title:            #文章标题
categories:       #文章分类
tags:             #文章标签
  - Hexo
  - Github
date: 2016-12-15  #日期
---
这之后就是文章正文了
```
写文章本人采用[Markdown pad 2](http://markdownpad.com/)


