<p align="center">
  <img src="https://cloud.githubusercontent.com/assets/2059754/24601246/753a7f36-1858-11e7-9d6b-7a0e64fb27f7.png" alt="bash logo"/>
</p>

本 Repo 翻译自 [Adnan Ahmed](https://github.com/Idnan) 的 [bash-guide](https://github.com/Idnan/bash-guide)

## 目录

  1. [基础操作](#1-基础操作)
    1.1. [文件操作](#11-文件操作)

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

## 1.1. 文件操作

<table>
   <tr>
      <td><a href="#a-cat">cat</a></td>
      <td><a href="#b-chmod">chmod</a></td>
      <td><a href="#c-cp">cp</a></td>
      <td><a href="#d-diff">diff</a></td>
      <td><a href="#e-file">file</a></td>
      <td><a href="#f-find">find</a></td>
      <td><a href="#g-gunzip">gunzip</a></td>
      <td><a href="#h-gzcat">gzcat</a></td>
      <td><a href="#i-gzip">gzip</a></td>
      <td><a href="#j-head">head</a></td>
   </tr>
   <tr>
      <td><a href="#k-lpq">lpq</a></td>
      <td><a href="#l-lpr">lpr</a></td>
      <td><a href="#m-lprm">lprm</a></td>
      <td><a href="#n-ls">ls</a></td>
      <td><a href="#o-more">more</a></td>
      <td><a href="#p-mv">mv</a></td>
      <td><a href="#q-rm">rm</a></td>
      <td><a href="#r-tail">tail</a></td>
      <td><a href="#s-touch">touch</a></td>
   </tr>
</table>

### a. `cat`

可以在 UNIX 或 Linux 下用于以下目的。

* 在屏幕上显示文本文件
* 复制文本文件
* 合并文本文件
* 创建文本文件

```bash
cat filename
cat file1 file2
cat file1 file2 > newcombinedfile
cat < file1 > file2 # 复制 file1 到 file2
```

### b. `chmod`

更改文件的读取、写入和执行权限。

```bash
chmod -options filename
```

### c. `cp`

将文件从一个位置复制到另一个位置。

```bash
cp filename1 filename2
```

`filename1` 文件的源路径，`filename2` 是文件的目标路径。

### d. `diff`

比较文件，并列出它们的差异。

```bash
diff filename1 filename2
```

### e. `file`

确定文件类型。

```bash
file filename
```

实例：

```bash
$ file index.html
 index.html: HTML document, ASCII text
```

### f. `find`

在目录中查找文件。

```bash
find directory options pattern
```

实例：

```bash
$ find . -name README.md
$ find /home/user1 -name '*.png'
```

### g. `gunzip`

解压用 gzip 压缩的文件。

```bash
gunzip filename
```

### h. `gzcat`

查看被 gzip 压缩的文件，而不必使用 gunzip 解压它。

```bash
gzcat filename
```

### i. `gzip`

压缩文件。

```bash
gzip filename
```

### j. `head`

输出文件的前10行。

```bash
head filename
```

### k. `lpq`

查看打印机队列。

```bash
lpq
```

实例：

```bash
$ lpq
Rank    Owner   Job     File(s)                         Total Size
active  adnanad 59      demo                            399360 bytes
1st     adnanad 60      (stdin)                         0 bytes
```

### l. `lpr`

打印文件。

```bash
lpr filename
```

### m. `lprm`

从打印机队列中删除某些内容。

```bash
lprm jobnumber
```

### n. `ls`

列出您的文件。`ls` 有许多选项：`-l` 以 "长格式" 列出文件，其中包含文件的精确大小，谁拥有该文件，谁有权查看它，以及上次修改时间。`-a` 列出所有文件，包括隐藏文件。有关此命令的详细信息，请查看此[链接](https://ss64.com/bash/ls.html)。

```bash
ls option
```

实例：

<pre>
$ ls -la
rwxr-xr-x   33 adnan  staff    1122 Mar 27 18:44 .
drwxrwxrwx  60 adnan  staff    2040 Mar 21 15:06 ..
-rw-r--r--@  1 adnan  staff   14340 Mar 23 15:05 .DS_Store
-rw-r--r--   1 adnan  staff     157 Mar 25 18:08 .bumpversion.cfg
-rw-r--r--   1 adnan  staff    6515 Mar 25 18:08 .config.ini
-rw-r--r--   1 adnan  staff    5805 Mar 27 18:44 .config.override.ini
drwxr-xr-x  17 adnan  staff     578 Mar 27 23:36 .git
-rwxr-xr-x   1 adnan  staff    2702 Mar 25 18:08 .gitignore
</pre>

### o. `more`

显示文件的第一部分（按空格移动，按 q 退出）。

```bash
more filename
```

### p. `mv`

将文件从一个位置移动到另一个位置。

```bash
mv filename1 filename2
```

`filename1` 文件的源路径，`filename2` 是文件的目标路径。

此外，它可以用于重命名文件。

```bash
mv old_name new_name
```

### q. `rm`

删除文件。在目录上使用此命令会给出错误提示。
`rm: directory: is a directory`
要删除一个目录，您必须通过 `-r` 标志，它将递归地删除目录的内容。
或者可以使用 `-f` 标志强制删除，即无任何确认信息等。

```bash
rm filename
```

### r. `tail`

输出文件的最后 10 行。当文件增长时，使用 `-f` 输出追加的数据。

```bash
tail filename
```

### s. `touch`

创建或更新文件。

```bash
touch filename
```

实例：

```bash
$ touch trick.md
```

## 贡献

- 报告问题
- 提交合并请求
- 推广宣传

## 许可

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/deed.zh)
