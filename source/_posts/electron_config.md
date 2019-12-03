---
title: Electron 用法介绍
date: 2019-10-12 14:52:26
tags: [config]
comments: true
toc: true
reward: false
---

Electron是GitHub开发的一个开源框架。它允许使用Node.js和Chromium完成桌面GUI应用程序的开发。Electron现已被多个开源Web应用程序用于前端与后端的开发，著名项目包括GitHub的Atom和微软的Visual Studio Code。

官方网站：https://electronjs.org/
中文教程：https://weishuai.gitbooks.io/electron-/

<!--more-->


## 环境搭建

#### 1. 安装 `electron`

```bash
# 全局安装
$ npm install -g electron
$ npm i -D electron@latest

# 安装在项目下
$ npm install --save-dev electron
```

#### 2. 关于安装慢的问题

- 通过`npm`命令配置

   ```bash
   # 全局设置下载源：
   $ npm config set registry https://registry.npm.taobao.org
   
   # 然后将electron包下载地址注册位淘宝的镜像:
   $ npm config set ELECTRON_MIRROR https://npm.taobao.org/mirrors/electron/
   ```

- 通过写配置文件

  找到你的个人目录里面的.npmrc文件打开文件写入下面的配置：

  ```bash
  registry=https://registry.npm.taobao.org/
  ELECTRON_MIRROR=http://npm.taobao.org/mirrors/electron/
  ```
  
- 通过cnpm安装

  ```bash
  $ sudo npm install -g cnpm --registry=https://registry.npm.taobao.org
  $ cnpm install
  ```

#### 3. 手动搭建一个 `electron`项目

- 新建一个项目目录，例如: `electron-demo`
- 使用`npm init`生成`package.json`
- 在 `electron-demo` 目录下面新建文件: `index.html`、`main.js` `
- 在`index.html` 里面用 `css` 进行布局(以前怎么写现在还是怎么写)
- 在 `main.js` 中写如下代码：

```bash
const electron = require('electron'); //electron 对象的引用
// 控制应用生命周期的模块。
const {app} = electron;
// 创建原生浏览器窗口的模块。
const {BrowserWindow} = electron;

// 保持一个对于 window 对象的全局引用，如果你不这样做，
// 当 JavaScript 对象被垃圾回收， window 会被自动地关闭
let mainWindow=null;

function createWindow() {
  // 创建浏览器窗口。
  mainWindow = new BrowserWindow({width: 800, height: 600});

  // 加载应用的 index.html。
  mainWindow.loadURL('index.html');

  // 启用开发工具。
  // mainWindow.webContents.openDevTools();

  // 当 window 被关闭，这个事件会被触发。
  mainWindow.on('closed', () => {
    // 取消引用 window 对象，如果你的应用支持多窗口的话，
    // 通常会把多个 window 对象存放在一个数组里面，
    // 与此同时，你应该删除相应的元素。
    mainWindow = null;
  });
}

// Electron 会在初始化后并准备
// 创建浏览器窗口时，调用这个函数。
// 部分 API 在 ready 事件触发后才能使用。
app.on('ready', createWindow);

// 当全部窗口关闭时退出。
app.on('window-all-closed', () => {
  // 在 macOS 上，除非用户用 Cmd + Q 确定地退出，
  // 否则绝大部分应用及其菜单栏会保持激活。
  if (process.platform !== 'darwin') {
    app.quit();
  }
});

app.on('activate', () => {
  // 在 macOS 上，当点击 dock 图标并且该应用没有打开的窗口时，
  // 绝大部分应用会重新创建一个窗口。
  if (mainWindow === null) {
    createWindow();
  }
});

// 在这文件，你可以续写应用剩下主进程代码。
// 也可以拆分成几个文件，然后用 require 导入。
```

#### 4. 快速示例

```bash
# 克隆示例项目的仓库
$ git clone https://github.com/electron/electron-quick-start

# 进入这个仓库
$ cd electron-quick-start

# 安装依赖并运行
$ npm install && npm start
```

#### 5. 运行

[electron-prebuilt](https://github.com/electron-userland/electron-prebuilt) 是一个 `npm` 模块，包含所使用的 Electron 预编译版本。 如果你已经用 `npm` 全局安装了它，你只需要按照如下方式直接运行你的应用：`electron .`

如果你是局部安装，那么运行`./node_modules/.bin/electron .`