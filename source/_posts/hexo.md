---
title: 使用 Hexo 搭建 Github 博客
---
看着大家都在写博客，我也终于忍不住了。
这是我的第一篇博文，记录了使用hexo+github搭建博客的方法，以及过程中遇到的问题和解决方案。
也是告诉自己不忘初心，持之以恒！

## 搭建博客

### 1. 准备工作

- 安装[git](https://git-scm.com/downloads)，[node.js](https://nodejs.org/zh-cn/download/)，和[hexo](https://hexo.io/zh-cn/docs/index.html)
- 验证各安装版本：
``` bash
$ node -v
$ npm -v
$ hexo -v
```

### 2. 初始化 Blog

- 安装 Hexo 完成后，执行下列命令，会在指定文件夹中新建所需要的文件：
``` bash
$ hexo init <folder> 
$ cd <folder>
$ npm install
```
- 执行下列命令，可以查看在本地预览：
``` bash
$ hexo g   # 生成静态页面
$ hexo s  # 启动本地 blog 服务器
```
打开浏览器，在地址栏输入 <u>localhost:4000</u>，就可以查看本地博客了

### 3. 同步 Hexo 到 Github
- 新建 Github 项目，命名为 XXX.github.io，XXX 为自己的GitHub 用户名。
- 打开本地文件夹内的 <code>_config.yml</code> 配置文件，进行如下修改：
``` bash
deploy:
  type: git
  repository: https://github.com/XXX/XXX.github.io.git
  branch: master
```
- 运行以下命令：
``` bash
$ npm install hexo-deployer-git –save  # 安装 hexo-deployer-git
$ hexo g  # 本地生成静态文件
$ hexo d  # 将本地静态文件推送至Github
```
此时，打开浏览器，访问 http://XXX.github.io

### 4. 添加 ssh key 到 GitHub
- 检查 ssh key 是否存在，如果存在可以跳过下一步：
``` bash
$ ls -al ~/.ssh
```
- 生成新的 ssh key：
``` bash
$ ssh-keygen -t rsa -C "your_email"
```
默认会在相应路径下（<code>~/.ssh/id_rsa.pub</code>）生成<code>id_rsa</code>私钥文件和<code>id_rsa.pub</code>公钥文件，私钥不要公开或者上传，公钥可以上传至github进行验证。

- 将ssh key添加至 Github

用终端打开 <code>id_rsa.pub</code>，复制内容，进入 github ->settings ->ssh and gpg keys ->new ssh key 粘贴。

### 5. 更换主题
- 在[Hexo](https://hexo.io/themes/) 官网上选择感兴趣的主题，将主题项目拷贝到 themes 文件夹下：
``` bash
$ cd <folder>
git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia
```

- 修改 <code>_config.yml</code>，将主题设置为 yilia
``` bash
theme: yilia
```

&nbsp;
## 问题一：多终端同步 Hexo
- hexo 的原理
``` bash
$ hexo clean  # 清理你的项目缓存
$ hexo g  # 将你刚刚编写的md编译为浏览器可以识别的html
$ hexo d  # 发布到远程仓库
```
hexo d 是发布到 <code>_config.yml</code> 中配置的branch分支上（一般都是master主分支），所以就可以将 hexo 主文件（未编译的）放到另一个仓库中，更新文章时，只需再将这个仓库提交一下就可以了。

- 开始
``` bash
# 将更改的文件加入 git 仓库中
$ git add source 
$ git commit -m "your desciption"

# 新建 hexo 分支
$ git branch hexo

# 切换到 hexo 分支
$ git checkout hexo

# 将本地与 Github 项目对接
$ git remote add origin https://github.com/yourname/yourname.github.io.git

# push 到 Github 项目的 hexo 分支上
$ git push origin hexo
```
至此，hexo主站程序上传到hexo分支了，发布文章时，正常流程写md，<code>hexo clean</code>，<code>hexo g -d</code>就可以啦~

- 另外一个终端更新
``` bash
# 将Github中hexo分支clone到本地
$ git clone https://github.com/XXX/XXX.github.io.git

# cheackout 远程代码到本地hexo分支
$ git checkout -b hexo origin/hexo

# 注意，这里一定要切换到刚刚clone的文件夹内执行，安装必要的所需组件，不用再init
$ npm install

# 新建一个.md文件，并编辑完成自己的博客内容
$ hexo new post "new blog name"

# 经测试每次只要更新source中的文件到Github中即可，因为只是新建了一篇新博客
$ git add source
$ git commit -m "your desciption"

# 更新分支
$ git push origin hexo
# push更新完分支之后将自己写的博客对接到自己搭的博客网站上，同时同步了Github中的master
$ hexo d -g
```

- 每次切换终端时，记得先执行 git pull origin hexo 将本地与远程同步哦～
&nbsp;
## 问题二：新换 theme 无法同步远程

刚开始我的主题是 next，后来嫌弃它太单调了，就换成了现在的主题，但是发现 push 不上去了，于是开始各种 Google。
终于找到了可靠的解决方案。[原文链接点这里](https://pangjunpeng.com/2018/03/22/%E6%80%BB%E7%BB%93%E4%B8%80%E4%B8%8B%E8%BF%99%E5%87%A0%E5%A4%A9%E6%90%AD%E5%8D%9A%E5%AE%A2%E9%81%87%E5%88%B0%E7%9A%84%E9%97%AE%E9%A2%98%EF%BC%9A%E5%A4%9A%E7%BB%88%E7%AB%AF%E6%9B%B4%E6%96%B0hexo%EF%BC%8Cthems%E4%B8%BB%E9%A2%98%E6%8F%90%E4%BA%A4%E4%B8%8D%E4%B8%8A%E5%8E%BB%E7%AD%89/)
由于 themes 中 yilia 是 clone 的，所以不在我的版本库中，自然也就 push 不上去。
需要删除 .git 文件夹，重新 <code>add commit push</code>。

``` bash
$ git rm -rf --cached themes/yilia
$ git add themes/yilia/*
$ git commit
$ git push
```

在此感谢提供各种解决方法的博主们～
出现的问题其实还有一些，但是 Google 就够了，以后继续加油吧！