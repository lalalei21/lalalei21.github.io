---
title: vscode配置和vue环境搭建
date: 2019-11-12 14:52:26
tags: [config]
comments: true
toc: true
reward: false
---

**Visual Studio Code** (简称 VS Code / VSC) 是一款免费开源的现代化轻量级代码编辑器，支持几乎所有主流的开发语言的语法高亮、智能代码补全、自定义快捷键、括号匹配和颜色区分、代码片段、代码对比 Diff、GIT命令 等特性，支持插件扩展，并针对网页开发和云端应用开发做了优化。
**Vue**是一套用于构建用户界面的渐进式框架，具体用法详见[官网](https://cn.vuejs.org/)。
<!--more-->

## 1. Vscode配置

- 下载安装:
    1. ubuntu : 
    
    ```
    sudo add-apt-repository ppa:ubuntu-desktop/ubuntu-make
    sudo apt-get update
    sudo apt-get install ubuntu-make
    umake web visual-studio-code
    
    ```
    2. windows : https://code.visualstudio.com/Download

- 主题：  
    1. 颜色主题：One Dark Pro
    2. 文件图标主题：Seti

- 插件：  
    1. Auto Close Tag -  自动闭合HTML标签
    2. Auto Rename Tag - 自动修改匹配的标签
    3. HTML Snippets - 超级实用且初级的 H5代码片段以及提示
    4. HTML CSS Support - css提示（支持vue) , 新版已经支持scss文件检索
    5. JavaScript (ES6) code snippets - ES6语法代码段
    6. ESLint - 代码检查
    7. Path AutoComplete - 路径自动补全
    8. vetur - 语法高亮、智能感知、Emmet等  
    9. VueHelper - snippet代码片段
    10. Bracket Pair Colorizer - 对括号对进行着色
    11. Path Intellisense - 路径提示器
    12. GitLens - 显示文件最近的commit和作者，显示当前行commit信息
    13. Git History(git log) - 查看git log
    14. python
    15. code runner

- 用户设置：shift+ctrl+p -> user setting

```
{
    "editor.fontSize": 16,
    "editor.fontFamily": "Consolas, 'Courier New', monospace,'宋体'",
    "workbench.colorTheme": "One Dark Pro",
    "editor.lineHeight": 26,
    "editor.tabSize": 2,
    "editor.detectIndentation":true,
    "extensions.autoUpdate": true,
    "editor.renderLineHighlight": "none",
    "editor.letterSpacing": 1,
    "window.zoomLevel": 0,
    "eslint.validate": [
        "javascript",
        "javascriptreact",
        "html",
        "vue",
        {
            "language": "html",
            "autoFix": true
        }
    ],
    "http.proxy": "http://dev-proxy.oa.com:8080",
    "emmet.syntaxProfiles": {
        "javascript":"jsx",
        "vue-html":"html",
        "vue":"html"
    },
    "eslint.options": {
        "plugins":["html"]
    },
    "window.openFilesInNewWindow": "on",
    "workbench.iconTheme": "vscode-great-icons",
    "workbench.editor.enablePreview": false,
    "window.restoreWindows": "all",
    "python.pythonPath": "/usr/bin/python3",
    "code-runner.runInTerminal": true,
    "code-runner.saveAllFilesBeforeRun": true,
    "gitlens.advanced.messages": {
        "suppressCommitHasNoPreviousCommitWarning": false,
        "suppressCommitNotFoundWarning": false,
        "suppressFileNotUnderSourceControlWarning": true,
        "suppressGitVersionWarning": false,
        "suppressLineUncommittedWarning": false,
        "suppressNoRepositoryWarning": false,
        "suppressUpdateNotice": false,
        "suppressWelcomeNotice": false
    },
    "explorer.confirmDelete": false
}

{
  "version": "0.1.0",
  "command": "python3",
  "isShellCommand": true,
  "args": ["${file}"],
  "showOutput": "always"
}

{
    "editor.fontSize": 13,
    "editor.fontFamily": "Source Code Pro, Monaco, Menlo, 'Courier New', monospace,'宋体'",
    "workbench.colorTheme": "Quiet Light",
    "editor.lineHeight": 22,
    "editor.tabSize": 2,
    "editor.detectIndentation":true,
    "extensions.autoUpdate": true,
    "editor.renderLineHighlight": "none",
    "editor.letterSpacing": 0.2,
    "window.zoomLevel": 0,
    "emmet.syntaxProfiles": {
        "javascript":"jsx",
        "vue-html":"html",
        "vue":"html"
    },
    "window.openFilesInNewWindow": "on",
    "workbench.iconTheme": "vscode-great-icons",
    "workbench.editor.enablePreview": false,
    "window.restoreWindows": "all",
    "python.pythonPath": "/usr/local/bin/python3.7",
    "code-runner.runInTerminal": true,
    "code-runner.saveAllFilesBeforeRun": true,
    "gitlens.advanced.messages": {
        "suppressFileNotUnderSourceControlWarning": true,
        "suppressShowKeyBindingsNotice": true
    },
    "explorer.confirmDelete": false
}

{
  "python.pythonPath": "/usr/local/bin/python3.7"
}

```

- 快捷键

**F1** 或 **Ctrl+Shift+P**: 打开命令面板。在打开的输入框内，可以输入任何命令，例如：

1. 按一下 Backspace 会进入到 Ctrl+P 模式
2. 在 Ctrl+P 下输入 > 可以进入 Ctrl+Shift+P 模式


在 **Ctrl+P** 窗口下还可以:

1. 直接输入文件名，跳转到文件  
2. ? 列出当前可执行的动作  
3. ! 显示 Errors或 Warnings，也可以 Ctrl+Shift+M  
4. : 跳转到行数，也可以 Ctrl+G 直接进入  
5. @ 跳转到 symbol（搜索变量或者函数），也可以 Ctrl+Shift+O 直接进入  
6. @ 根据分类跳转 symbol，查找属性或函数，也可以 Ctrl+Shift+O 后输入:进入  
7. \# 根据名字查找 symbol，也可以 Ctrl+T  


ctrl + alt + - : 后退  
ctrl + alt + + : 前进  
ctr + shift + ` : 打开终端
ctr + shift + [/] : 折叠/展开代码

&nbsp;
## 2. Vue环境搭建

![image](http://upload-images.jianshu.io/upload_images/3868852-dc56e16bc1ae6b13.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 安装node.js  
> 从nodejs官网(http://nodejs.cn/download/)下载安装包 

- 获取nodejs模块安装目录访问权限
    ```
    sudo chmod 777 /usr/local/lib/node_modules/
    ```

- 安装淘宝镜像

    ```
    npm install -g cnpm --registry=https://registry.npm.taobao.org
    ```
- 安装webpack

    ```
    cnpm install webpack -g
    ```

- 安装vue脚手架

    ```
    npm install vue-cli -g
    ```

- 进入一个目录，根据模板创建项目

    ```
    vue init webpack-simple 工程名字<工程名字不能用中文>
    //或者创建 vue1.0 的项目
    vue init webpack-simple#1.0 工程名字<工程名字不能用中文>
    ```
- 安装项目依赖，安装 vue 路由模块vue-router和网络请求模块vue-resource，启动

    ```
    npm install
    cnpm install vue-router vue-resource --save
    npm run dev
    ```