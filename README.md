<p align="center">
  <img src="https://cloud.githubusercontent.com/assets/2059754/24601246/753a7f36-1858-11e7-9d6b-7a0e64fb27f7.png" alt="bash logo"/>
</p>

本 Repo 翻译自 [Adnan Ahmed](https://github.com/Idnan) 的 [bash-guide](https://github.com/Idnan/bash-guide)

## 目录

  1. [基础操作](#1-基础操作)

# 1. 基础操作

### a. `export`

显示所有环境变量。如果想要获取具体变量的细节，执行 `echo $VARIABLE_NAME`。

```bash
export
```

实例：

```bash
$ export
AWS_HOME=/Users/adnanadnan/.aws
LANG=en_US.UTF-8
LC_CTYPE=en_US.UTF-8
LESS=-R

$ echo $AWS_HOME
/Users/adnanadnan/.aws
```

### b. `whatis`

显示用户命令、系统调用、库函数或其他在手册页面中的描述。

```bash
whatis something
```

实例：

```bash
$ whatis bash
bash (1)             - GNU Bourne-Again SHell
```

### c. `whereis`

使用系统自动构建的数据库来搜索可执行文件、源文件和手册页面。

```bash
whereis name
```

实例：

```bash
$ whereis php
/usr/bin/php
```

### d. `which`

在环境变量 PATH 指定的目录中搜索可执行文件。此命令将输出可执行文件的绝对路径。

```bash
which program_name
```

实例：

```bash
$ which php
/c/xampp/php/php
```

### e. `clear`

清除窗口上的内容。

## 贡献

- 报告问题
- 提交合并请求
- 推广宣传

## 许可

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/deed.zh)
