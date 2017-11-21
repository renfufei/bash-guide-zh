<p align="center">
  <img src="https://cloud.githubusercontent.com/assets/2059754/24601246/753a7f36-1858-11e7-9d6b-7a0e64fb27f7.png" alt="bash logo"/>
</p>

本 Repo 翻译自 [Adnan Ahmed](https://github.com/Idnan) 的 [bash-guide](https://github.com/Idnan/bash-guide)

## 目录

  1. [基础操作](#1-基础操作)
    1.1. [文件操作](#11-文件操作)
    1.2. [文本操作](#12-文本操作)
    1.3. [目录操作](#13-目录操作)
    1.4. [SSH、系统信息和网络操作](#14-ssh系统信息和网络操作)
  2. [基础 Shell 编程](#2-基础shell编程)
    2.1. [变量](#21-变量)

# 1. 基础操作

### a. `export`

显示所有环境变量。如果想要获取具体变量的细节，执行 `echo $VARIABLE_NAME`。

```bash
export
```

实例：

```bash
$ export
declare -x CLASSPATH=".:/usr/local/jdk1.8.0_74/lib:/usr/local/jdk1.8.0_74/jre/lib:"
declare -x HISTCONTROL="ignoredups"
declare -x HISTSIZE="1000"
declare -x JRE_HOME="/usr/local/jdk1.8.0_74/jre"
declare -x LANG="en_US.UTF-8"
declare -x PATH="/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin"

$ echo $PATH
/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin
```

### b. `whatis`

显示用户命令、系统调用、库函数或其他在手册页面中的描述。

```
whatis 需要查询的名称
```

实例：

```bash
$ whatis bash
bash (1)             - GNU Bourne-Again SHell


$ whatis whatis
whatis (1)           - display manual page descriptions

```

### c. `whereis`

使用系统自动构建的数据库来搜索可执行文件、源文件和手册页面。

```
whereis 可执行命令名称
```

实例：

```bash
$ whereis php
/usr/bin/php

whereis javac
javac: /usr/local/jdk1.8.0_74/bin/javac

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

which javac
/usr/local/jdk1.8.0_74/bin/javac

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

## 1.2. 文本操作

<table>
    <tr>
      <td><a href="#a-awk">awk</a></td>
      <td><a href="#b-cut">cut</a></td>
      <td><a href="#c-echo">echo</a></td>
      <td><a href="#d-egrep">egrep</a></td>
      <td><a href="#e-fgrep">fgrep</a></td>
      <td><a href="#f-fmt">fmt</a></td>
      <td><a href="#g-grep">grep</a></td>
      <td><a href="#h-nl">nl</a></td>
      <td><a href="#i-sed">sed</a></td>
      <td><a href="#j-sort">sort</a></td>
   </tr>
   <tr>
      <td><a href="#k-tr">tr</a></td>
      <td><a href="#l-uniq">uniq</a></td>
      <td><a href="#m-wc">wc</a></td>
   </tr>
</table>

### a. `awk`

awk is the most useful command for handling text files. It operates on an entire file line by line. By default it uses whitespace to separate the fields. The most common syntax for awk command is

awk 是处理文本文件时最有用的命令。它一行一行地在整个文件上运行。默认情况下，它使用空格分隔字段。awk 命令最常用的语法是

```bash
awk '/search_pattern/ { action_to_take_if_pattern_matches; }' file_to_parse
```

让我们看下面的文件`/etc/passwd`。以下是此文件包含的示例数据：

```
root:x:0:0:root:/root:/usr/bin/zsh
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
```

现在, 让我们从这个文件中只获得用户名。`-F` 指定我们将在哪个基础上分隔字段。在本示例是 `:`。`{ print $1 }` 表示输出出第一个匹配字段。

```bash
awk -F':' '{ print $1 }' /etc/passwd
```

运行上述命令后，将得到以下输出。

```
root
daemon
bin
sys
sync
```

有关如何使用 `awk` 的更多详细信息，查看[链接](https://www.cyberciti.biz/faq/bash-scripting-using-awk)。

### b. `cut`

从文件的每行中删除部分

*example.txt*

```
red riding hood went to the park to play
```

*采用空格作为分隔符，显示第 2、7 和 9 列*

```bash
cut -d " " -f2,7,9 example.txt
```

```bash
riding park play
```

### c. `echo`

显示一行文本

*显示 "Hello World"*

```bash
echo Hello World
```

```bash
Hello World
```

*隔行显示 "Hello World" 的各单词*

```bash
echo -ne "Hello\nWorld\n"
```

```bash
Hello
World
```

### d. `egrep`

输出匹配模式的行 - 扩展表达式（'grep -E' 的别名）

Print lines matching a pattern - Extended Expression (alias for: 'grep -E')

*example.txt*

```
Lorem ipsum
dolor sit amet,
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

*显示有 “Lorem” 或有 “dolor” 的行*

```bash
egrep '(Lorem|dolor)' example.txt
```

或者

```bash
grep -E '(Lorem|dolor)' example.txt
```

```bash
Lorem ipsum
dolor sit amet,
et dolore magna
duo dolores et ea
sanctus est Lorem
ipsum dolor sit
```

### e. `fgrep`

输出匹配模式的行 - 固定模式匹配（'grep -F' 的别名）

*example.txt*

```
Lorem ipsum
dolor sit amet,
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
foo (Lorem|dolor)
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

*在 example.txt 中查找确切的字符串 '(Lorem|dolor)'*

```bash
fgrep '(Lorem|dolor)' example.txt
or
grep -F '(Lorem|dolor)' example.txt
```

```bash
foo (Lorem|dolor)
```

### f. `fmt`

简单的最佳文本格式化程序

*实例： example.txt（1 行）*

```
Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
```

*将 example.txt 输出为每行 20 个字符的宽度*

```bash
cat example.txt | fmt -w 20
```

```bash
Lorem ipsum
dolor sit amet,
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

### g. `grep`

查找文件内的文本。可以使用 grep 搜索一个或多个正则表达式匹配的文本行，并仅输出匹配的行。

```bash
grep pattern filename
```

实例：

```bash
$ grep admin /etc/passwd
_kadmin_admin:*:218:-2:Kerberos Admin Service:/var/empty:/usr/bin/false
_kadmin_changepw:*:219:-2:Kerberos Change Password Service:/var/empty:/usr/bin/false
_krb_kadmin:*:231:-2:Open Directory Kerberos Admin Service:/var/empty:/usr/bin/false
```

您也可以使用 `-i` 选项强制 grep 忽略字母大小写。`-r` 可用于搜索指定目录下的所有文件，例如：

```bash
$ grep -r admin /etc/
```

还有 `-w` 仅搜索单词。有关 `grep` 的更多细节，查看[链接](https://www.cyberciti.biz/faq/grep-in-bash)。

### h. `nl`

计算文件内容行号。

*example.txt*

```
Lorem ipsum
dolor sit amet,
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

*显示 example.txt 内容和行号*

```bash
nl -s". " example.txt
```

```bash
     1. Lorem ipsum
     2. dolor sit amet,
     3. consetetur
     4. sadipscing elitr,
     5. sed diam nonumy
     6. eirmod tempor
     7. invidunt ut labore
     8. et dolore magna
     9. aliquyam erat, sed
    10. diam voluptua. At
    11. vero eos et
    12. accusam et justo
    13. duo dolores et ea
    14. rebum. Stet clita
    15. kasd gubergren,
    16. no sea takimata
    17. sanctus est Lorem
    18. ipsum dolor sit
    19. amet.
```

### i. `sed`

用于过滤和转换文本的流编辑器。

*example.txt*

```
Hello This is a Test 1 2 3 4
```

*用连字符替换所有空格*

```bash
sed 's/ /-/g' example.txt
```

```bash
Hello-This-is-a-Test-1-2-3-4
```

*用“d”替换所有数字*

```bash
sed 's/[0-9]/d/g' example.txt
```

```bash
Hello This is a Test d d d d
```

### j. `sort`

对文本文件的行排序。

*example.txt*

```bash
f
b
c
g
a
e
d
```

*排序 example.txt*

```bash
sort example.txt
```

```bash
a
b
c
d
e
f
g
```

*随机排序 example.txt*

```bash
sort example.txt | sort -R
```

```bash
b
f
a
c
d
g
e
```

### k. `tr`

转换或删除字符。

*example.txt*

```
Hello World Foo Bar Baz!
```

*将所有小写字母转换为大写字母*

```bash
cat example.txt | tr 'a-z' 'A-Z'
```

```bash
HELLO WORLD FOO BAR BAZ!
```

*将所有空格转换为换行符*

```bash
cat example.txt | tr ' ' '\n'
```

```bash
Hello
World
Foo
Bar
Baz!
```

### l. `uniq`

报告或省略重复行。

*example.txt*

```bash
a
a
b
a
b
c
d
c
```

*只显示 example.txt 的唯一行（首先你需要排序，否则看不到重叠）*

```bash
sort example.txt | uniq
```

```bash
a
b
c
d
```

*显示每行的唯一项，并告诉我找到了多少个实例*

```bash
sort example.txt | uniq -c
```

```bash
    3 a
    2 b
    2 c
    1 d
```

### m. `wc`

告诉你一个文件中有多少行，单词和字符。

```bash
wc filename
```

实例：

```bash
$ wc demo.txt
7459   15915  398400 demo.txt
```

其中，`7459` 是行数，`15915` 是单词数量，`398400` 是字符数量。

## 1.3. 目录操作

<table>
   <tr>
      <td><a href="#a-cd">cd</a></td>
      <td><a href="#b-mkdir">mkdir</a></td>
      <td><a href="#c-pwd">pwd</a></td>
   </tr>
</table>

### a. `cd`

使你从一个目录移动到其他目录。运行这个

```bash
$ cd
```

使你移动到主目录。此命令接受一个可选的 `dirname`，它将使你移动到该目录。

```bash
cd dirname
```

### b. `mkdir`

创建一个目录。

```bash
mkdir dirname
```

### c. `pwd`

告诉你当前所在的目录。

```bash
pwd
```

## 1.4. SSH、系统信息和网络操作

<table>
   <tr>
      <td><a href="#a-bg">bg</a></td>
      <td><a href="#b-cal">cal</a></td>
      <td><a href="#c-date">date</a></td>
      <td><a href="#d-df">df</a></td>
      <td><a href="#e-dig">dig</a></td>
      <td><a href="#f-du">du</a></td>
      <td><a href="#g-fg">fg</a></td>
      <td><a href="#h-finger">finger</a></td>
      <td><a href="#i-kill">kill</a></td>
      <td><a href="#j-killall">killall</a></td>
   </tr>
   <tr>
      <td><a href="#k-last">last</a></td>
      <td><a href="#l-man">man</a></td>
      <td><a href="#m-passwd">passwd</a></td>
      <td><a href="#n-ping">ping</a></td>
      <td><a href="#o-ps">ps</a></td>
      <td><a href="#p-quota">quota</a></td>
      <td><a href="#q-scp">scp</a></td>
      <td><a href="#r-ssh">ssh</a></td>
      <td><a href="#s-top">top</a></td>
      <td><a href="#t-uname">uname</a></td>
   </tr>
   <tr>
      <td><a href="#u-uptime">uptime</a></td>
      <td><a href="#v-w">w</a></td>
      <td><a href="#w-wget">wget</a></td>
      <td><a href="#x-whoami">whoami</a></td>
      <td><a href="#y-whois">whois</a></td>
   </tr>
</table>

### a. `bg`

列出已停止或在后台运行的作业；恢复在后台已停止的作业。

### b. `cal`

显示日历。

### c. `date`

显示当前的日期和时间。

### d. `df`

显示磁盘使用情况。

### e. `dig`

获取域名的 DNS 信息。

```bash
dig domain
```

### f. `du`

显示文件或目录的磁盘使用情况。有关此命令的详细信息查看[链接](http://www.linfo.org/du.html)。

```bash
du [option] [filename|directory]
```

选项：

- `-h` （人类可读）以千字节 (K)、兆字节 (M) 和千兆字节 (G) 显示输出。
- `-s` （摘要）输出目录的总磁盘空间和子目录的简报。

实例：

```bash
du -sh pictures
1.4M pictures
```

### g. `fg`

将最近的后台作业放到前台运行。

### h. `finger`

显示用户的信息。

```bash
finger username
```

### i. `kill`

杀死 （结束）给定 ID 的进程

```bash
kill PID
```

### j. `killall`

使用名称来杀死一组进程。

```bash
killall processname
```

### k. `last`

列出指定用户的过去登入信息。

```bash
last yourUsername
```

### l. `man`

显示指定命令的手册。

```bash
man command
```

### m. `passwd`

允许现在登入用户更改它的密码。

### n. `ping`

Ping 主机并输出结果。

```bash
ping host
```

### o. `ps`

列出进程。

```bash
ps -u yourusername
```

### p. `quota`

显示你的磁盘配额是多少。


```bash
quota -v
```

### q. `scp`

在本地主机和远程主机之间或两台远程主机之间传输文件。

*从本地主机复制到远程主机*

```bash
scp source_file user@host:directory/target_file
```

*从远程主机复制到本地主机*

```bash
scp user@host:directory/source_file target_file
scp -r user@host:directory/source_folder farget_folder
```

此命令还接受一个可用于连接到特定端口的选项 `-P`。

```bash
scp -P port user@host:directory/source_file target_file
```

### r. `ssh`

ssh (SSH 客户端) 是一个在远程机器上登录和执行命令的程序。

```bash
ssh user@host
```

此命令还接受一个可用于连接到特定端口的选项 `-p`。

```bash
ssh -p port user@host
```

### s. `top`

显示当前活动的进程。

### t. `uname`

显示内核信息。

```bash
uname -a
```

### u. `uptime`

显示当前的正常运行时间。

### v. `w`

显示谁在线。

### w. `wget`

下载文件。

```bash
wget file
```

### x. `whoami`

返回现在登入用户的用户名。

### y. `whois`

获取域名的 whois 信息。

```bash
whois domain
```

# 2. 基础 Shell 编程

在 bash 脚本文件中编写的第一行称为 `shebang`。任何脚本中的这一行确定脚本的执行能力，如独立的可执行文件，而不用在终端中预先键入 sh，bash，python，php 等。

```shell
#!/bin/bash
```

## 2.1. 变量

在 bash 中创建变量与其他语言类似。没有数据类型。bash 中的变量可以包含数字、字符、字符串等。你无需声明变量，只需为其引用赋值就会创建它。

实例：

```bash
str="hello world"
```

上面一行创建了一个变量 `str`，并将 “hello world” 赋值给它。将 `$` 放在变量名的开头来获取变量的值。

实例：

```bash
echo $str   # hello world
```

## 贡献

- 报告问题
- 提交合并请求
- 推广宣传

## 许可

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/deed.zh)
