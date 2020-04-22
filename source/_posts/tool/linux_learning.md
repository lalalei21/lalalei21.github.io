---
title: Linux 学习笔记
date: 2018-6-12 14:52:26
tags:
  - linux
categories:
  - 啦啦蕾的学习笔记～
  - 工具使用
---

### 常见用法
```bash
command -options arguments
```
- date 显示当前时间
- cal 显示日历
- df 查看磁盘剩余空间数量
- free 显示空闲内存数量
- exit 结束终端会话
- pwd 显示当前路径
- ls 列出目录内容
- cd 更改目录
- file 确定文件类型
- cp 复制文件和目录
- mv 移动/重命名文件和目录
- mkdir 创建目录
- rm 删除文件和目录
- ln 创建硬链接和符号链接
- type 显示一个命令的类型
- which 显示一个可执行程序的位置
- help 得到 shell 内建命令的帮助文档
- man 显示命令手册页
- apropos 显示一系列适合的命令
- info 显示命令info
- whatis 显示一个命令的简洁描述
- alias 创建命令别名

### I/O 重定向

- cat － 连接文件
- sort － 排序文本行
- uniq － 报道或省略重复行
- grep － 打印匹配行
- wc － 打印文件中换行符，字，和字节个数
- head － 输出文件第一部分
- tail - 输出文件最后一部分
- tee - 从标准输入读取数据，并同时写到标准输出和文件

### 研究长格式输出
```bash
drwxr-xr-x@  5 zhenglei  staff   160  8  4 16:04 lalala
```
| 字段 | 含义 |
| --- | --- |
| drwxr-xr-x@ | 对于文件的访问权限。第一个字符指明文件类型。在不同类型之间， 开头的“－”说明是一个普通文件，“d”表明是一个目录。其后三个字符是文件所有者的 访问权限，再其后的三个字符是文件所属组中成员的访问权限，最后三个字符是其他所 有人的访问权限。 |
| 5 | 文件的硬链接数目 |
| zhenglei | 文件所有者的用户名。 |
| staff | 文件所属用户组的名字。 |
| 96 | 以字节数表示的文件大小。 |
| 16:04 | 上次修改文件的时间和日期。 |
| lalala | 文件名 |


### tail 命令语法
```bash
tail [ -f ] [ -c Number | -n Number | -m Number | -b Number | -k Number ] [ File ]
```
- 参数解释：
`-f` 该参数用于监视File文件增长。
`-c Number` 从 Number 字节位置读取指定文件
`-n` Number 从 Number 行位置读取指定文件。
`-m` Number 从 Number 多字节字符位置读取指定文件，比方你的文件假设包括中文字，假设指定-c参数，可能导致截断，但使用-m则会避免该问题。
`-b Number` 从 Number 表示的512字节块位置读取指定文件。
`-k Number` 从 Number 表示的1KB块位置读取指定文件。
`File` 指定操作的目标文件名称
上述命令中，都涉及到number，假设不指定，默认显示10行。Number前面可使用正负号，表示该偏移从顶部还是从尾部開始计算。
tail可运行文件一般在`/usr/bin/`以下。
<p></p>

- 示例：
```bash
tail -f filename
```
说明：监视filename文件的尾部内容（默认10行，相当于增加参数 -n 10），刷新显示在屏幕上。退出，按下CTRL+C。
```bash
tail -n 20 filename
```
说明：显示filename最后20行。
```bash
tail -f -n 10 filename
```
说明：逆序显示filename最后10行。
<p></p>

- 补充
跟`tail`功能相似的命令还有：
`cat` 从第一行開始显示档案内容。
`tac` 从最后一行開始显示档案内容。
`more` 分页显示档案内容。
`less` 与 `more` 相似，但支持向前翻页
`head` 仅仅显示前面几行
`tail` 仅仅显示后面几行
`n` 带行号显示档案内容
`od` 以二进制方式显示档案内容
