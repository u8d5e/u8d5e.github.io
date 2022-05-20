---
slug: docusaurus-github-pages
title: docusaurus部署Github Pages搭建个人博客
authors:
  name: cz
  title: ITcoder
  url: https://github.com/u8d5e
  image_url: https://avatars.githubusercontent.com/u/58099851?v=4
tags: [docusaurus, github pages]
---

# docusaurus部署Github Pages搭建个人博客

起因是这样的，一次偶然，我发现了博客的魅力，以及各种大佬的炫酷博客，我被深深地震撼到了，一直以来，因为这样那样的事没能开始搭建博客的道路（~~啊我...是了，是我拖延~~😭）身边朋友给我推荐了ducusaurus，说比较简单，容易上手，成功部署后，确实深感操作简单，容易上手，值得推荐👍

<!-- truncate -->

## 预备工作

首先需要有如下必要以及非必要软件，在此贴上官方下载网址

鉴于贴上相关教程不一定跟上最新版本，具体下载及其配置教程就自行搜索吧（~~没错我懒，就没贴，狗头保命~~）

1. [下载node.js](https://nodejs.org/zh-cn/download/)

2. [下载vscode](https://code.visualstudio.com/)（非必须）

3. [下载git](https://git-scm.com/)

4. 安装yarn

   命令1：`yarn：npm install -g yarn --registry=https://registry.npm.taobao.org`

5. 配置yarn源

   命令1：`yarn config set registry https://registry.npm.taobao.org -g`

   命令2：`yarn config set sass_binary_site http://cdn.npm.taobao.org/dist/node-sass -g`

6. [git命令备忘清单](https://training.github.com/downloads/zh_CN/github-git-cheat-sheet/)（非必须）

## 关于docusaurus

[docusaurus](https://www.docusaurus.io/)是基于React框架的静态站点生成器，可快速生成一个文档网站，可用于打造自己的博客等

项目结构如下：

![img](https://api2.mubu.com/v3/document_image/d6271053-ff7d-405e-a2dd-f988a08189e5-1683730.jpg)

关于详细介绍也可参考官网指南[点击这里😄](https://docusaurus.io/zh-CN/docs)

## 安装docusaurus

也可参考官网指南：[docusaurus官网指南](https://docusaurus.io/zh-CN/docs)

1. **创建新的 Docusaurus 站点：**

命令1：`npx create-docusaurus@latest my-website classic`

`my-website`是创建名，可随意更改，如我设置为`cz-blog`

`classic`是经典主题，我未更改，如有所需，可参考官网指南

2. **运行网站：**

命令1：`cd my-website`

命令2：`npm run start`或`yarn run start`

退出快捷键：`ctrl`+`c`

默认情况浏览器会自动打开新窗口 http://localhost:3000 页面如下![img](https://api2.mubu.com/v3/document_image/4f8db090-cee7-4d9a-899d-75e127463b7d-1683730.jpg)

3. **构建站点**

命令1：`npm run build`或`yarn run build`

4. 更新docusaurus（非必须）

命令1：`npm install`或`yarn install`或`yarn upgrade @docusaurus/core@latest @docusaurus/preset-classic@latest`

5. 检测版本（非必须）

命令1：npx docusaurus --version

## 部署github pages

1. **github创建USERNAME.github.io仓库**

   ![img](https://api2.mubu.com/v3/document_image/58c2a35f-e0bb-4e06-8d37-a6655aa35402-1683730.jpg)

2. **github中git命令创建仓库**

创建新仓库

```git
git init
git add README.md
git commit -m "first commit"
git branch -M master
git remote add origin git@github.com:u8d5e/u8d5e.github.io.git
git push -u origin master
```

推送已存在的仓库

```git
git remote add origin git@github.com:u8d5e/u8d5e.github.io.git
git branch -M master
git push -u origin master
```

3. **github新建分支gh-pages**

![img](https://api2.mubu.com/v3/document_image/b5af7e69-30a8-4694-889f-43ce0d62d59c-1683730.jpg)

4. **github设置部署分支**![img](https://api2.mubu.com/v3/document_image/ff938aff-ff98-451c-bb0e-0a1193cdd21b-1683730.jpg)

5. 本地测试构建（非必须）

命令1：`npm run serve或yarn run serve`

站点默认为部署在 http://localhost:3000/

## 修改docusaurus相关文档

1. **跳转到创建文档的目录，打开项目代码**![img](https://api2.mubu.com/v3/document_image/e7330669-3dbf-484c-89f8-7e15cdaae9ab-1683730.jpg)

命令1：`code .`

会自动打开 vscode （或自己常用IDE）展示代码

2. **docusaurus.config.js设置**

![image-20220520142033812](C:\Users\〇语\AppData\Roaming\Typora\typora-user-images\image-20220520142033812.png)



```html
  title: 'cz-blog', // The title of the website
  tagline: 'show me your code', // A word on the front page
  url: 'https://u8d5e.github.io/', // Your website URL
  baseUrl: '/',
  onBrokenLinks: 'throw',
  onBrokenMarkdownLinks: 'warn',
  favicon: 'img/cat4.png',

  // GitHub pages deployment config.
  // If you aren't using GitHub pages, you don't need these.
  organizationName: 'u8d5e', // Usually your GitHub org/user name.
  projectName: 'u8d5e.github.io', // Usually your repo name.
  deploymentBranch: 'gh-pages',
  trailingSlash: false,
```

> 注意：u8d5e是我的用户名，请自行更改

## yarn命令部署

命令：`yarn deploy`

最终如下图所示即成功部署![img](https://api2.mubu.com/v3/document_image/bc7c05ce-1ce1-4f6b-9d70-b240ff9ad8bc-1683730.jpg)

等那么一会会（一般1-2min），浏览器输入`https://用户名.github.io/`网址就可以看到效果了，如我的网址：[Hello from cz-blog](https://u8d5e.github.io/)

## bug小结

我起先用vscode自带终端，报错不断，问题连连😵，用window的cmd运行一步到位，一错未有😄，目前还未深究这两者造成不同效果的区别，如有大佬指点，在此不甚感激💖！

**问题如下**

### OpenSSL SSL_read: Connection was aborted, errno 10053

修改默认存储大小`git config --global http.postBuffer 524288000`

又报新错，出现下一个问题😭

### Failed to connect to github.com port 443 after 21114 ms: Timed out

关闭vpn（没用😭）

全局设置、取消全局设置（没用😭）

网上查阅的解决办法解决后又报上一个错（被bug玩弄于股掌之中既视感😭）

重新设置代理模式（http远程地址改用了git的，有用了一半😂，部署中终止，出现下一个问题😭）![img](https://api2.mubu.com/v3/document_image/0225d27c-6455-4c97-9ec8-a0c422b7027a-1683730.jpg)

### 非快进问题non-fast-forward

![img](https://api2.mubu.com/v3/document_image/f70136a4-072b-448f-8db8-f688f3481fd0-1683730.jpg)

```git
git fetch origin
git merge origin BANCH_NAME
git pull origin BANCH_NAME
git push origin BANCH_NAME
```

查阅官网提供以上方法，出现下一个问题😭

### 本地与远程不匹配faild to push some refs to xxx

![img](https://api2.mubu.com/v3/document_image/f1730384-22ae-47a7-b4bc-0a1d1180f502-1683730.jpg)

设置上游分支：`git branch --set-upstream-to=origin/<远程分支> <本地分支>`

取消上游分支：`git branch --unset-upstream`

查看上游分支：`git status`、`git checkout <分支>`、`git branch -vv`

感觉弄明白bug源头了，但是未解决😭



> **删库重来N次**😵（~~只要重来的次数够多，bug就能解决完，~~bushi）跟朋友交流后我决定用纯命令来部署，没想到，一次成功了，流下了充（bu）满（xue）技（wu）术的泪水😭



成功后，修改docusaurus默认文档中blog文档后，再次`yarn deploy`出现了新的问题😭

### FATAL ERROR: Zone Allocation failed - process out of memory # error Command failed with exit code 3221225725.

关闭vpn（💖解决）

> 这个问题搜索出来各种回答不适用，我结合自己小飞机不断突然断掉，又出现过关闭vpn能解决问题的回答（上面第二个bug搜索出来过这个解决办法），尝试了关闭vpn再部署，成功了💖

## 最终效果

blog网址：[Hello from cz-blog](https://u8d5e.github.io/)

会继续学习前端，丰富自己的blog的~~

## ![img](https://api2.mubu.com/v3/document_image/fc11d568-56d2-4eca-85f2-e3399eea9f14-1683730.jpg)![img](https://api2.mubu.com/v3/document_image/2da2f9a8-65fa-47e7-a01a-6077c45cbdd1-1683730.jpg)