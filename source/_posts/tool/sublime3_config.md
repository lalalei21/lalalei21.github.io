---
title: Sublime3 配置
date: 2017-5-4 14:52:26
tags:
  - sublime
categories:
  - 啦啦蕾的学习笔记～
  - 工具使用
---
> Sublime Text 是一款流行的代码编辑器软件，也是HTML和散文先进的文本编辑器，可运行在Linux，Windows和Mac OS X。也是许多程序员喜欢使用的一款文本编辑器软件。

<!--more-->

### 安装
<style>
ol{
  margin-bottom: 10px;
}
</style>
- ubuntu: 
  1. 添加sublime text 3的仓库：sudo add-apt-repository ppa:webupd8team/sublime-text-3
  2. 更新软件库：sudo apt-get update
  3. 安装Sublime Text 3:sudo apt-get install sublime-text-installer

- windows：官网下载安装即可。
- 3126 注册码

```
—– BEGIN LICENSE —–
Michael Barnes
Single User License
EA7E-821385
8A353C41 872A0D5C DF9B2950 AFF6F667
C458EA6D 8EA3C286 98D1D650 131A97AB
AA919AEC EF20E143 B361B1E7 4C8B7F04
B085E65E 2F5F5360 8489D422 FB8FC1AA
93F6323C FD7F7544 3F39C318 D95E6480
FCCC7561 8A4A1741 68FA4223 ADCEDE07
200C25BE DBBC4855 C4CFB774 C5EC138C
0FEC1CEF D9DCECEC D3A5DAD1 01316C36
—— END LICENSE ——
```

### 安装内部插件
  使用`Package Control`组件安装：   
  - 按<kbd>Ctrl + `</kbd>调出console，粘贴以下代码到底部命令行并回车
  ```python
  import urllib.request,os; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ','%20')).read()) 
  ```
  - 在`Perferences->package settings`中看到`package control`这一项，则安装成功。
  - <kbd>Ctrl + Shift + P</kbd>调出命令面板

#### Emmet : 一种快速编写html/css的方法

- 注意：安装`Emmet`的同时，也会自动安装其依赖PyV8 binary库。
- 安装不了则手动[下载1](https://github.com/emmetio/pyv8-binaries#readme)/[下载2](http://www.qingzz.cn/sublimeText_Emmet_PyV8)，下载完成后解压，文件夹重命名为linux64-p3，将文件夹拷贝到 Installed Packages/PyV8/，文件夹里面有两个文件 _PyV8.cpython-33m.so 和 PyV8.py。
- [使用见官网](https://docs.emmet.io/cheat-sheet/)


#### Theme - Spacegray
- [使用见官网](http://kkga.github.io/spacegray/)
- 参考配置
```json
{
	"color_scheme": "Packages/Theme - Spacegray/base16-ocean.dark.tmTheme",
	"highlight_line": true,
	"line_padding_bottom": 5,
	"line_padding_top": 5,
	"spacegray_sidebar_font_xlarge": true,
	"spacegray_sidebar_tree_large": true,
	"spacegray_tabs_auto_width": true,
	"spacegray_tabs_font_large": true,
	"spacegray_tabs_xlarge": true,
	"theme": "Spacegray.sublime-theme",
	"spacegray_fileicons": true,
	"enable_tab_scrolling": false,
	"font_face": "Consolas",
	"font_size":11,
}
```

#### BracketHighlighter** ：括号配对
- [使用见官网](http://facelessuser.github.io/BracketHighlighter/)
- `Pregerence > Package Settings > BracketHighlighter > Bracket Settings - User`
- `{} － curly  () － round  [] － square <> － angle “” ‘’ － quote`
- `style: solid、underline、outline、highlight`

#### sublimeCodeIntel ： 代码自动补全