# Chapter1 基本命令

## 1. 基本操作

### 1.1 路径操作

> type `cd <path>` to set current work directory.

### 1.2 文件操作

#### Show infomation of dir

> list all of files and dirs with file in white and dir in blue. Show more info with params.

``` bash
$ ls [Params]
```

##### Params

| Params | Description                                                  |
| ------ | ------------------------------------------------------------ |
| -l     | show more info of file with order:  **Authority Number Accoount Size Last_Modify** |
| -u     | show last query time, followed behind -l                     |
| -c     | show last modify time, followed behind -l                    |
| -a     | show all files and dirs **include hidden**                   |
| -h     | show info in a more readable way(show headline)              |
| -d     | show info instead of content of current directory            |
| -R     | show children directory in recursion                         |
| -F     | show file type description                                   |
| --help | show help information                                        |

---

#### Renew time

> Renew the time of files, and create new file in current directory if not exists. Input more filenames to create multiple files in one time.

```bash
$ touch filenames [Params]
```

##### Params

| Params | Funtions                     |
| ------ | ---------------------------- |
| -a     | Just modify query time       |
| -m     | Just modify modify time      |
| -c     | Don't create when not exists |

---

#### Remove file

```bash
$ rm dirnames [Params]
```

Remove one and more files. 

> **Tip:** Use “-r” for delete diretory with files. 

##### Param

| Params | Desciption                                         |
| ------ | -------------------------------------------------- |
| -i     | Ask for operation                                  |
| -I     | Ask for operation when there are more than 3 files |
| -f     | Not asking for operation                           |
| -r     | Recursion delete files                             |
| --help | show help information                              |

---

#### Copy file

```bash
$ cp source_path target_path [Params]
```

Copy files(That means source_path can be multiple files)  from source to target. And add a symbol“/” to copy a directory. 

> **Tip:** Use pattern like “`*`” to modern matching, like “`file*`” means all files with a name beginning with “`file`”.

##### Params

| Params | Desciption                                            |
| ------ | ----------------------------------------------------- |
| -i     | Ask for overwrite                                     |
| -f     | Don't ask for overwrite if exists                     |
| -R     | Recursion copy for source directory                   |
| -b     | Set up backup files with files name starting with `~` |
| -v     | show operation results                                |
| --help | show help information                                 |

---

#### Move file

```bash
$ mv source_path target_path [Params]
```

Move file from source_path to target_path, and its usage is roughly the same as `cp`.

##### Param

| Params | Desciption                                            |
| ------ | ----------------------------------------------------- |
| -i     | Ask for overwrite                                     |
| -f     | Don't ask and overwrite default                       |
| -b     | Set up backup files with files name starting with `~` |
| -v     | show operation results                                |
| --help | show help information                                 |

---

#### Make directory

> Create a new directory at target path.

```bash
$ mkdir dirnames [Params]
```

##### Param

| Params | Desciption                      |
| ------ | ------------------------------- |
| -i     | Ask for overwrite               |
| -m 777 | Create with specified authority |
| -p     | Create directory in recursion   |
| --help | show help information           |

---

#### Remove directory

> Remove a **empty** directory at target path.

```bash
$ rmdir dirnames [Params]
```

##### Param

| Params | Desciption                                         |
| ------ | -------------------------------------------------- |
| -i     | Ask for operation                                  |
| -I     | Ask for operation when there are more than 3 files |
| -f     | Not asking for operation                           |
| -p     | Delete directory in recursion                      |
| --help | show help information                              |

---

### 1.3 文件权限操作

#### Description

> Author description for info of `ls -l` . User tag means file operation local user has, group means users on net other than local user, others means user other than above.

![03-01-02.png](/home/hedge/Tools/typora_images/03-01-02.png)

> **Type:** File type with “d” and directory with “-”
>
> **Operate authority:** `rwx` description like above. 

#### chmod

```bash
$ chmod [option] [authority] file
```

> Change authority of spectified user to file through string or number denotion.

> **Tip: There is no “-” in fact, just for readability.**

For python, you can add an authority and add one line like following to execute directly

```bash
#! usr/bin/python
```

#### umask

> User can set authority mask for file through umask.

```bash
$ umask [option] [code]
```

| Params | Description             |
| ------ | ----------------------- |
| -S     | show in string denotion |



## 2. 二级操作

### 2. 文件操作

#### Concate

> `Cat` can just read file with just one source_file, or overwrite /  append characters of source to target, even concate data several file to a new.

```bash
$ cat source_file [op  target_file]
```

##### Params

| Params | Desciption                                    |
| ------ | --------------------------------------------- |
| -A     | show all characteristic including unprintable |
| -n     | enumberate and show line number               |
| -b     | same to -n but enumberate skip blank line     |
| -s     | compress continual space to one               |

##### Op

| Op   | Description    |
| ---- | -------------- |
| >    | Overwrite mode |
| >>   | Append mode    |

---

#### More

> `more`命令用于分屏显示文件内容而非打印，常用于长文本的显示，同时浏览到结尾时自动退出，相比之下交互性不如`less`。

```bash
$ more option file
```

| Params | Desciption                        |
| ------ | --------------------------------- |
| -p     | clear screen instead of scrolling |
| -s     | compress continual space to one   |
| +n     | show file from line n             |
| +/str  | show file from line with str      |

##### 分屏操作基本说明

| 按键  | 功能             |
| ----- | ---------------- |
| Enter | 下一行           |
| Space | 下一页           |
| b     | 上一页           |
| /str  | 查找字符串       |
| n     | 查找下一个字符串 |
| q     | 退出             |

---

#### Less

> `less`命令与`more`命令基本相同，但同时浏览到结尾时不会自动退出，相比之下交互性更强。

```bash
$ less option file
```

---

#### Word Count

> 用于显示文件的字节数、字数和行数。

```bash
$ wc option file
```

| 可选项 | 功能         |
| ------ | ------------ |
| -c     | 只统计字节数 |
| -l     | 只统计行数   |
| -m     | 只统计字符数 |
| -w     | 只统计字数   |

---

#### Sort

> sort命令是个常用的文字处理命令，它将文本文件的各行按照ASC字符顺序由小到大排序，并输出排序后的结果。未指定文件时，读标准输入文件。

```bash
$ sort [option] [file]
```

| 选项 | 功能                                  |
| ---- | ------------------------------------- |
| -b   | 忽略开始的空白                        |
| -d   | 只考虑数字、字母和空格                |
| -f   | 忽略大小写                            |
| -kn  | 从第n个字段开始的内容作为排序的关键字 |
| -r   | 逆序排序                              |

---

#### **Find**

> **Search file** with **certain** condition in directory.

```bash
$ find [directory] [express] [operation] 
```

| 表达式            | 功能                                                |
| ----------------- | --------------------------------------------------- |
| -name filename    | 搜索名字为filename的文件，支持通配符模式            |
| -user name        | 查找用户name所拥有的文件                            |
| -group name       | 查找用户组name所拥有的文件                          |
| -mtine [+-]n      | 查找在n天前修改过的文件                             |
| -atine [+-]n      | 查找在n天前访问过的文件                             |
| -ctine [+-]n      | 查找在n天前创建的文件                               |
| -mmin [+-]n       | 查找在n分钟前修改过的文件                           |
| -amin [+-]n       | 查找在n分钟前访问过的文件                           |
| -cmin [+-]n       | 查找在n分钟前创建的文件                             |
| -type x           | 查找类型为x的文件                                   |
| -size [+-]n[cbkw] | 查找文件大小超过n的文件，单位为[c字节b块k千字节w字] |
| -a                | 逻辑与                                              |
| -o                | 逻辑或                                              |
| !/-not            | 逻辑非                                              |
| \\(express\\)     | 优先表达式                                          |

| 操作类型                  | 功能                       |
| ------------------------- | -------------------------- |
| -print                    | 显示搜到的文件名（默认）   |
| -ls                       | 显示文件的详细信息         |
| -exec <u>command</u> {} \ | 对找到的文件执行命令       |
| -ok <u>command</u> {} \   | 对找到的文件执行命令并询问 |

**示例**

```shell
# 删除路径下所有文件名以.gz结尾的文件
$ find . -name "*.gz" -type f -exec rm -fr {} \;
```

---

#### **Grep**

> Search text files for matching strings and show line

```bash
$ grep [option] match [file]
```

| 选项 | 功能                         |
| ---- | ---------------------------- |
| -v   | 列出不包含匹配字符串的行     |
| -c   | 不显示匹配的行，只显示结果   |
| -l   | 只显示含有匹配字符串的文件名 |
| -r   | 递归搜索每一个文件及其子目录 |
| -n   | 在每个匹配行前加序号显示     |
| -i   | 不区分大小写匹配             |
| -w   | 匹配整个单词而不是某一部分   |

---

#### Sed

> Perform specific operation to lines of file according to condition.

##### Flag

```bash
$ sed [-hnV][-e<script>][-f<script文件>][文本文件]
```

##### Param

> - -e<script>或--expression=<script> 以选项中指定的script来处理输入的文本文件。
> - -f<script文件>或--file=<script文件> 以选项中指定的script文件来处理输入的文本文件。
> - -h或--help 显示帮助。
> - -n或--quiet或--silent 仅显示script处理后的结果。
> - -V或--version 显示版本信息。

Action：

> - a ：新增， a 的后面可以接字串，而这些字串会在新的一行出现(目前的下一行)～
> - c ：取代， c 的后面可以接字串，这些字串可以取代 n1,n2 之间的行！
> - d ：删除，因为是删除啊，所以 d 后面通常不接任何东东；
> - i ：插入， i 的后面可以接字串，而这些字串会在新的一行出现(目前的上一行)；
> - p ：打印，亦即将某个选择的数据印出。通常 p 会与参数 sed -n 一起运行～
> - s ：取代，可以直接进行取代的工作哩！通常这个 s 的动作可以搭配正规表示法！例如 1,20s/old/new/g 就是啦！

##### Instance

将 /etc/passwd 的内容列出并且列印行号，同时，请将第 2~5 行删除！

```bash
$ nl /etc/passwd | sed '2,5d'
```

----

#### Awk

> awk是一种编程语言，用于在linux/unix下根据给定条件对文本和数据中进行指定的操作处理。数据可以来自标准输入(stdin)、一个或多个文件，或其它命令的输出。它支持用户自定义函数和动态正则表达式等先进功能，它在命令行中使用，但更多是作为脚本来使用，更多内容参见[此处](http://c.biancheng.net/view/992.html)。
>
> 相比于 grep 和 sed
>
> -  grep 更适合单纯的查找或匹配文本
> -  sed 更适合编辑匹配到的文本
> -  awk 更适合格式化文本，对文本进行较复杂格式处理

##### awk语法说明

**基本表达**

```shell
$ awk [option] 'condition {action}' [file]
```

**语法形式**

```shell
$ awk [options] 'script' var=value file(s)
$ awk [options] -f scriptfile var=value file(s)
```

**常用命令选项**

- -F fs   fs指定输入分隔符，fs可以是字符串或正则表达式，如-F:
- -v var=value   赋值一个用户定义变量，将外部变量传递给awk
- -f scripfile  从脚本文件中读取awk命令

**语法结构**

awk是由*pattern*和*action*组成， pattern 表示 AWK 在数据中查找的内容，而 action 是在找到匹配内容时所执行的一系列命令.

```shell
$ awk '{pattern + action}' {filenames}
```

pattern 可以是如下几种或者什么都没有（全部匹配）：

- /正则表达式/：使用通配符的扩展集。
- 关系表达式：使用运算符进行操作，可以是字符串或数字的比较测试。
- 模式匹配表达式：用运算符~（匹配）和~!（不匹配）。
- BEGIN语句块、pattern语句块、END语句块：参见awk的工作原理

action 由一个或多个命令、函数、表达式组成，之间由换行符或分号隔开，并位于大括号内，可以是如下几种，或者什么都没有（print）

- 变量或数组赋值
- 输出命令
- 内置函数
- 控制流语句

##### awk常见应用和工作原理

下面列出一个最常用的awk命令结构，借此分析原理

```shell
$ awk 'BEGIN{ commands } pattern{ commands } END{ commands }'
```

- 首先执行 `BEGIN {commands}` 内的语句块，注意这只会执行一次，经常用于变量初始化，头行打印一些表头信息，只会执行一次，在通过stdin读入数据前就被执行；
- 从文件内容中读取一行，注意**awk是以行为单位处理的，每读取一行使用** **`pattern{commands}`** **循环处理** 可以理解成一个for循环，这也是最重要的部分；
- 最后执行 `END{ commands }` ,也是执行一次，在所有行处理完后执行，一帮用于打印一些统计结果。

第一个例子，获得/etc/passwd文件种每行的地1个和第7个数据，以逗号分隔，并再第一行和最后一行打印一串文字。

```shell
shell> $ cat /etc/passwd |awk  -F ':'  'BEGIN {print "name,shell"}  {print $1","$7} END {print "blue,/bin/nosh"}'
name,shell
root,/bin/bash
daemon,/usr/sbin/nologin
bin,/usr/sbin/nologin
sys,/usr/sbin/nologin
...
blue,/bin/nosh
```

**书写注意事项**

- awk后的命令需要用 单引号括起来
- 最好用 ‘{}’ 括起来每个部分，便于阅读；
- 每个 ‘{}’ 可以有多个命令或者其它，之间用 ‘;’ 号分割。

##### 怎么清晰的输出想要的信息？

awk的输出主要靠 `print`,`printf` 指令，这两个指令的用法和c语言中的 `print，printf` 一毛一样。awk处理每行时是以列为每个域，例如 `print $1` 就是输出第一列，`print $1,$2` 就是输出第1、2列，`print $0` 输出全部。

awk怎么区分列呢，默认是以空格区分，但是你也可以通过 `-F` 参数指定，例如 `-F;` 指定分号为分隔符，`-F[;,]` 指定分号和逗号为分隔符。

---

#### Cut



---







## 3. 短命令

> Alias to command. Modify the configuration file of zsh name `.zshrc` to set a alias.

**Command**

> vim .zshrc
>
> source .zshrc

**Add command to .zshrc**

> alias your_tag=‘command’

**Note :** 

> 1. No whitespace near ”=”;
> 2. Show all alias through command `alias` without any parameters; 



## 4. 开始菜单操作

operate through files: 

> ~/.local/share/applications
>
> /.config/menus
>
> /usr/share/application	---	user loaded package

delete accroding file just ok.



## 5. 其他操作

### 1. CPU state

```bash
$ top
```

### 2. Baloo Management

```bash
$ balooctl stop
$ balooctl disable
$ balooctl status
```

### 3. Install without sudo

非主机下载软件基本步骤包括：

```bash
$ wget url			# 或者apt-get download url
$ tar -xvf filename	# 解压.tar文件
$ cd filename		# 跳转目录
$ ./startfilename	# 运行安装bash文件
```



## 6. 解压与打包操作

### 6.1 Tar

Linux下常见的压缩包格式有5种:zip, tar.gz, tar.bz2, tar.xz, tar.Z，更多信息可以通过`tar --help`参数查看

其中tar是种打包格式,gz和bz2等后缀才是指代压缩方式:gzip和bzip2

```bash
$ tar -zxvf filename.tar.gz 	# .tar.gz
$ tar -jxvf filename.tar.bz2	# .tar.bz2
$ tar -Jxvf filename.tar.xz		# .tar.xz
$ tar -Zxvf filename.tar.Z*		# .tar.Z
```

其中tar命令参数分别如下：

| 选项参数 | 含义                 |
| -------- | -------------------- |
| z        | 压缩格式             |
| x        | 从备份文件中释放文件 |
| v        | 详细信息             |
| f        | 文件                 |
| r        | 递归执行命令         |
| t        | 列出备份文件的内容   |
| c        | 创建备份文件         |
| u        | 更新备份文件中的文件 |

其中z参数所在对应格式flag为：

| flag | 说明  |
| ---- | ----- |
| z    | gz    |
| j    | bzip2 |
| J    | xz    |
| Z    | Z     |

**事实上, 从1.15版本开始tar就可以自动识别压缩的格式,故不需人为区分压缩格式就能正确解压**

```bash 
$ tar -xvf <filename_tar.gz>	# 解压
$ tar -cf <archives_name> <files_to_archive>	# 打包文件
$ tar -uf <archives_name> <file>	# 更新打包文件中的某个文件
```

### 6.2 Zip

> ```shell
> $ zip -h	# for help
> $ zip [option] [target] [from]
> ```

| 参数 | 说明               |
| ---- | ------------------ |
| -q   | 安静模式           |
| -r   | 递归处理           |
| -S   | 包含系统及隐藏文件 |

### 6.3 rar

> ```shell
> $ rar -h			# for help
> $ rar a file 		# pack one file
> $ rar a -r archives files_to_pack	# pack a directory
> $ rar x [archives] file			# extract
> # note that there is not '-' before a/x;
> ```

### 6.4 gzip

> ```shell
> $ gzip -h;	# 查看帮助
> $ gzip <file> 	# 打包成gz文件
> $ gzip -d <file>	# 解压文件
> ```



## 汇总

> Here just show command and its function, its detailed parameters can be referred by.

| Command  | Description                                 |
| -------- | ------------------------------------------- |
| kill     | kill program                                |
| free     | check memory usage                          |
| ps       | report program status                       |
| pstree   | report in a tree data structure             |
| date     | show time                                   |
| shutdown | shutdown the system                         |
| w/who    | show user information logining in           |
| alias    | show all alias                              |
| unalias  | delete alias                                |
| grep     | search pattern in file                      |
| rgrep    | search in recursive                         |
| diff     | tell differece bewteen two files            |
| diffstat | according to diff, return size of diff      |
| file     | recognize type of file                      |
| find     | find file or dirctory                       |
| mv       | move or rename file                         |
| tee      | load data input then print to a file        |
| whereis  | search file                                 |
| which    | search file in $PATH                        |
| chattr   | change file attribute                       |
| chmod    | change mode/permission                      |
| cmp      | compare two files for if they are identical |
| cat      | concate one file to another                 |
| df       | show disk free                              |
| du       | show disk/directory usage                   |
| dd       | load file and output                        |





# Chapter2 系统操作

## 1. 包管理

### 1.1 pacman

> ArchLinux采用pacman作为默认的包管理，同时本机也安装有npm，一般情况下，不推荐使用npm，使用pacman包管理，部分使用差异仍在研究中。
>
> pacman命令手册可以通过以下命令查看，直接采用help参数可查看所有支持命令，带参数help可查看对应命令的详细说明。

```bash
$ sudo pacman --help
$ sudo pacman -S -h
```

> pacman包管理的主要命令包括9个，分别为：
>
> 1. -h(--help)：查看帮助手册
> 2. -V(--version)：查看pacman当前版本
> 3. -D(--database)：
> 4. -F(--files)：
> 5. **-Q(--query)**：查询当前已安装的包
> 6. **-R(--remove)**：删除当前已安装的包
> 7. **-S(--sync)**：安装或重装指定包
> 8. -T(--deptest)：
> 9. -U(--upgrade)：



### 1.2 yay

> **在AUR中安装软件包或应用程序**
>
> ```shell
> $ yay -S <package-name>
> ```
>
> **同时在官方存储库和AUR中搜索应用程序**
>
> ```shell
> $ yay -Ss <package-name>
> ```
>
> **只了解某个软件包的信息，则：**
>
> ```shell
> $ yay -Si <package-name>
> ```
>
> **安装本地软件包**
>
> ```shell
> $ yay -U <package-name>
> ```
>
> 也可以仅放置包装名称，它将搜索所有与标准相关的名称，并在列表中向我们显示找到的名称，并要求我们选择感兴趣的名称。
>
> ```shell
> $ yay <package-name>
> ```
>
> 检查更新项目
>
> ```shell
> $ yay -Pu
> ```
>
> **只同步数据库中的软件包**
>
> ```shell
> $ yay -Sy
> ```
>
> **执行系统更新**，同时也是布带参数默认执行的情况
>
> ```shell
> $ yay -Syu
> ```
>
> **更新系统，包括已安装的AUR软件包**
>
> ```shell
> $ yay -Syua
> ```
>
> 至 **安装任何没有提交的软件包** （当然，无需用户干预）
>
> ```shell
> $ yay -S --noconfirm <package-name>
> ```
>
> 消除不必要的依赖性
>
> ```shell
> $ yay -Yc
> ```
>
> **清除应用程序的缓存**，用于安装或更新无版本号更新的软件
>
> ```shell
> $ yay -Scc
> ```
>
> 单独删除软件包或应用程序
>
> ```shell
> $ yay -R <package-name>
> ```
>
> **删除软件包或应用程序及其依赖项**
>
> ```shell
> $ yay -Rs <package-name>
> ```
>
> 操作手册
>
> ```shell
> $ man yay
> ```



###  1.3 deb

> **注意debtap需要安装！**
>
> **实际上，deb并不是一个包管理，而是一个纯粹的安装工具！**因此，包的删除需要通过pacman实现。

```shell
$ sudo debtap -u 	# 更新debtap数据库
$ debtap xxx.deb	# 使用debtap转换deb包
$ sudo pacman -U xxx.pkg	# 使用pacman安装
```



## 2. 进程管理

### 2.1 进程查看命令

> 查看进程信息的命令是ps(progress status)命令。该命令可查看记录在进程PCB中的所有信息，默认情况下。该命令只显示本终端上运行的所有进程。

```bash
$ ps [option]	# show processes of selection
$ top 		# show running state of CPU in real time
```

| 选项   | 功能                     |
| ------ | ------------------------ |
| -e     | 显示所有进程             |
| -t tty | 显示终端tty上的进程      |
| -f     | 以全格式显示             |
| -o     | 以用户定义的格式显示     |
| a      | 显示所有终端上的所有进程 |
| u      | 以面向用户的格式显示     |
| x      | 显示所有不控制终端的进程 |
| -C cmd | 显示命令名为cmd的进程    |
| n      | 显示PID为n的进程         |

#### 字段含义

| 字段 | 含义                     | 字段  | 含义                |
| ---- | ------------------------ | ----- | ------------------- |
| PID  | 进程标识号               | TIME  | 进程累计使用CPU时间 |
| PPID | 父进程标识号             | STIME | 进程开始时间        |
| TTY  | 终端号，？表示不占用终端 | C     | 进程最近使用CPU时间 |
| UID  | 进程属主                 | CMD   | 进程执行的命令名    |

#### 用户格式

> 指定u选项时，以用户格式，分11列显示

| 字段    | 含义                            | 备注                                                         |
| ------- | ------------------------------- | ------------------------------------------------------------ |
| PID     | 标识号                          |                                                              |
| %CPU    | 进程占用CPU的时间与总运行时间比 |                                                              |
| %MEM    | 进程占用内存与总内存比          |                                                              |
| VSZ     | 进程虚拟内存的大小              | 以KB为单位                                                   |
| RSS     | 占用实际内存的大小              | 以KB为单位                                                   |
| STAT    | 进程当前状态                    | R 执行态<br />S 可中断睡眠态<br />D 不可中断<br />T 暂停态<br />Z 僵死态 |
| START   | 同STIME                         |                                                              |
| COMMAND | 同CMD                           |                                                              |



### 2.2 进程检索

```bash
$ pgrep modern
```

### 2.3 PID检索

```bash
$ pidof <name>
```

### 2.4 开机启动项

##### 1. 查看开机启动时间

```shell
$ systemd-analyze
```

##### 2.查看开机启动项及启动时间

```shell
$ systemd-analyze blame
```

##### 3.查看出错启动项

```shell
$ systemctl --all | grep not-found
```
##### 4.关闭出错启动项

```shell
$ systemctl <name>.service
```

##### 5.查看所有的服务项目

```shell
$ systemctl list-unit-files
```

## 3. 用户管理

### 1. 用户日志

> 有关用户登录的信息记录在 utmp(/var/run/utmp), wtmp(/var/log/wtmp), btmp(/var/log/btmp) 和 lastlog(/var/log/lastlog) 等文件中。
>
> 1. who、w 和 users 等命令通过 utmp(/var/run/utmp) 文件查询当前登录用户的信息。
> 2. last 和 ac 命令通过 wtmp(/var/log/wtmp) 文件查询当前与过去登录系统的用户的信息。
> 3. lastb 命令通过 btmp(/var/log/btmp) 文件查询所有登录系统失败的用户的信息。
> 4. lastlog 命令通过 lastlog(/var/log/lastlog) 文件查询用户最后一次登录的信息。

| Command | Params | Description                      |
| ------- | ------ | -------------------------------- |
| who     | -H, -q | 查看当前登陆的用户信息           |
| w       |        | 显示登陆的用户及其当前执行的任务 |
| users   |        | 显示当前登陆的用户的用户名       |
| last    |        | 显示至今的用户登陆信息           |
| lastb   |        | 显示所有登陆系统失败的用户信息   |
| lastlog |        | 显示用户最后一次登陆的信息       |
| ac      |        | 显示用户连接时间的统计数据       |

### 2. 新增用户帐号

> useradd 命令的用法是：
>
> ```shell
> $ useradd <user_name>
> ```
>
> 添加用户时，还有一些常用的选项：
>
> **选项名含义作用**
>
> -uUID手动为用户设置组 ID-ddirectory，家目录手工指定用户的家目录-ccomment，用户说明手工指定用户的说明，如果有空格，需要将说明文字用双引号括起来-ggroup，组名手工指定用户的初始组-Ggroup，组名手工指定用户的附加组，如果有多个附加组，用空格隔开-sshell，命令解释器手工指定用户的登录 shell，默认是 /bin/bash。

示例：

```powershell
luseradd -u 666 -d /superman -c "A good man" user2
#添加一个用户名是 user2 的用户，组 ID 是 666，家目录是 /superman，用户说明是“A good man”
```

### 3. 设置用户密码

新增用户后，还必须给用户设置一个密码用户才能正常登录。这时就要用到密码设置命令 passwd。

passwd 命令的语法格式是：`passwd [选项] [用户名]`，敲完这个命令后按下回车，系统会提示你输入密码。

root 用户可以修改任何用户的密码，只要在 passwd 后面跟相应的用户名即可。普通用户只能修改自己的密码，这时只要输入 passwd，然后回车就可以，后面无需跟用户名。

一般情况下 passwd 命令不需要加选项，但也有一些特殊情况需要用到选项，我们来看看 passwd 命令有哪些常用选项。

#### 查询用户的密码状态

我们用这个选项查看某个用户的密码状态：

![img](/home/hedge/Tools/typora_images/v2-417bad4a3675b4eadfc2bcda166a7114_r.jpg)

这里显示的信息其实就是 `/etc/shadow` 文件中用户 supermouse 的密码信息。

#### -l 锁定用户，-u 解锁用户

不难猜到，-l 是 lock 的意思，而 -u 就是 unclock。使用方式：

```powershell
passwd -l supermouse # 锁定用户
passwd -u supermouse # 解锁用户
```

锁定用户时，Linux 执行的操作其实就是在 shadow 文件中，该用户的密码前面加了两个感叹号。如图所示：

![img](/home/hedge/Tools/typora_images/v2-59a9a422769cc49a083839c6c1ca72c6_r.jpg)

![img](/home/hedge/Tools/typora_images/v2-e1d9c65332ad9106de0b95c6b1eff398_r.jpg)

所以也可以通过手工修改 shadow 文件的方式来锁定和解锁用户。

#### --stdin 使用字符串作为用户的密码

例如：

```powershell
echo "123" | passwd --stdin supermouse #将用户supermouse的密码设置为123
```

在 shell 编程的时候可能会用到这种方法，用于一次给多个用户设置初始密码。

----

### 4. 修改用户信息

usermod 命令的语法格式是：`usermod [选项] 用户名`

usermod 和 useradd 的功能类似，区别在于 usermod 命令的操作对象是已存在的用户，useradd 命令的操作对象是将要添加的新用户。正因如此，usermod 和 useradd 命令的部分选项是一样的。来看看 usermod 有哪些选项：

**选项含义功能**-uUID，用户 ID修改用户 ID-ccomment用户说明-GGID，附加组 ID定义用户所属的附加组，若有多个，用逗号分隔开-g初始组 ID修改用户的初始组，一般不建议修改-LLock临时锁定用户-UUnlock解除临时锁定

比如：

```powershell
uermod -c "General user" supermouse	# 修改用户supermouse的描述信息
```

### 5. 修改用户密码状态

chage 命令有两个常用的选项，`-l` 和 `-d`。`-l` 是查看用户密码信息，`-d` 是修改用户最后一修改密码的日期。

先看一下 `-l` 的执行效果：

![img](/home/hedge/Tools/typora_images/v2-e3cbcea5980741777b6ee34e5f15e20e_r.jpg)

`-d` 主要的用法是：

```powershell
chage -d 0 supermouse #将该用户最后一次修改密码的日期改成1970年1月1日，也就是把shadow文件的第3字段归0
```

这有什么作用呢？有时候，我们需要批量创建用户，并给这些用户设置一个初始密码，但是我们希望用户登录的时候将初始密码改掉，一遍增强系统的安全性。所以，只要我们将每个用户的最后一次修改密码的日期改成 1970 年 1 月 1 日，在他们首次登录时，系统会强制要求他们更改密码。

此外，chage 命令还有其他选项，这些选项本质上都是修改 `/etc/shadow` 文件，如下表所示：

**选项作用**-m两次密码修改间隔（shadow 文件第 4 字段）-M密码有效期（5字段）-W密码过期前警告天数（6字段）-I密码过后宽限天数（7字段）-E账号失效时间（8字段）

### 6. 删除用户

这个命令一般要加上 `-r` 选项，也就是这种格式：`userdel -r 用户名`。意思是，删除用户的同时删除该用户的家目录以及其他与该用户相关的文件。

### 7. 查看用户 ID 和用户所在的组的 ID

语法格式：`id 用户名`

![img](/home/hedge/Tools/typora_images/v2-1ecfda0a977006fb27e1cf35309fd8ce_r.jpg)

### 8. 用户切换命令

su 是 switch user 的简写，su 命令的一般用法是：`su - 用户名`，**注意：中间的那个短线不能省略，而且短线两侧有空格。**

其实如果不加中间的那个短线，该命令也能正常执行，只不过不是完全地切换用户，在执行某些命令的时候会报错，我们来看一下加短线与不加短线的区别。

这是不加短线的：

![img](/home/hedge/Tools/typora_images/v2-4b264f2b822b0623134fe5701a8e2c9e_720w.jpg)

没有报错，似乎已经切换到 root 用户了，但是我们来看一下此时的环境变量：

![img](/home/hedge/Tools/typora_images/v2-30bb01bcbec4f50e39e657d17aa22b55_r.jpg)

看图中圈出来的跟当前用户相关的部分，包括当前登录的用户名、家目录、用户邮箱等，还都是原来的 supermouse，而不是 root。

再来看加上短线的效果：

![img](/home/hedge/Tools/typora_images/v2-e871c8cfb25408c3e845034dfae49dbd_720w.jpg)

看一下环境变量：

![img](/home/hedge/Tools/typora_images/v2-4b5e17a6631dc0401ddace71a82f83e3_r.jpg)

这时才真正切换到 root 用户了。

而且你可能发现了，加短线与不加短线，是有区别的：

![img](/home/hedge/Tools/typora_images/v2-8507b57c732d8a99023d5c60246e675b_720w.jpg)

从这里我们也可以分辨出到底有没有真正切换到 root 用户。

从普通用户切换到 root 用户或者从普通用户切换到另一个普通用户需要输入密码，但是从 root 用户切换到普通用户不需要输入密码。

#### 以 root 用户的身份执行命令

还有一种场景，是我不需要切换到 root 用户，只需要用 root 权限执行一条命令，比如添加用户的命令 useradd。这时可以用 -c 选项。

```powershell
su - root -c "useradd user1" #以root用户的身份添加一个用户
```

### 9. 用户组管理命令

#### 9.1 添加用户组

语法格式：`groupadd [选项] 组名`

选项：-g GID 作用：指定组 ID

例：

```powershell
group flying #添加一个名为flying的组，组ID由系统默认生成
group -g 666 flying #添加一个名为flying的组，指定组ID是666
```

#### 9.2 修改用户组

语法格式：`groupmod [选项] 组名`

选项：

- -g GID 作用：修改组ID
- -n 新组名 作用：修改组名

例：

```powershell
groupmod -n fighting flying #将flying组改名为fighting
```

#### 9.3 删除用户组

语法格式：`groupdel 组名`

例：

```powershell
groupdel flying #删除flying组
```

需要注意的是，如果该组是某个用户的初始组，那么这个组无法被删除，因为如果把这个组删了，用户就没地方放了。如果没有用户将该组当做初始组，而只是把它当做附加组，那么这个组就可以被删除。

换句话说，如果某个组中有初始用户，则该组不能被删除，如果你执行删除组的命令，系统会报错；如果该组中只用附加用户，那么该组就可以被删除。

#### 9.4 把用户加入组或从组中删除

语法格式：`gpasswd [选项] 组名`

选项：

- -a 用户名 作用：把用户加入组
- -d 用户名 作用：把用户从组中删除

```powershell
gpasswd -a user1 root #把user1用户加入root组
gpasswd -d user3 root #把user3用户从root组中删除
```

这里执行的把用户加入组的操作，事实上是作为附加用户加入该组的，以上面那条命令为例，执行完该命令后，root 组其实是成为了 user1 用户的附加组。

把 user1 用户加入 root 组之后，我们查看一下 `/etc/group` 文件的内容：

![img](/home/hedge/Tools/typora_images/v2-09307e1a492e37f60fc51064064ab797_720w.jpg)

事实上，把用户加入组其实就是修改了这个文件，所以我们也可以通过修改这个文件的方式把某个用户加入某个组，比如如果我把文件第一行的内容改成这样：

![img](/home/hedge/Tools/typora_images/v2-cb19c13c7e02ee12838325855a7a8171_720w.jpg)

就表明我把 user2 用户（如果user2用户存在的话）也加入了 root组。同理，从组中删除用户也可以通过修改 `/etc/group` 文件的方式实现。



## 4. 字体管理

查看已安装字体

```
fc-list | less
```

搜索库里可用的字体

```
pacman -Ss ttf | less
```

找到要用的自体安装之，比如文泉忆

```
sudo pacman -S wqy-zenhei 
```

或者手动安装，把ttf字体文件复制到/usr/share/fonts/TTF目录下。

更新字体库

```
fc-cache -vf
```

删除直接删除字体文件即可，随后更新字体库。



## 5. 开关机

> 开关机的实现借助两个函数实现，两者皆可达到目的。

### 4.1 shutdown

> shutdown命令用于安全关闭Linux系统。

| 选项      | 说明                         |
| --------- | ---------------------------- |
| -t <time> | 延迟关机（min）              |
| -r        | 重启系统                     |
| -k        | 给所有登录用户发送警告信息   |
| -h        | 立刻关闭系统                 |
| -c        | 取消一个在运行的shutdown命令 |

### 4.2 halt

> halt命令是最简单关机命令，就是调用shutdown -h命令，杀死在运行程序并完成文件系统写操作后关闭系统。

### 4.3 reboot

### 4.4 init

### 4.5 poweroff

## 其他操作

### cal

> 显示当前的月份和日历。

```bash
$ cal [[月份]年份]
```

### man

> 以普通文本形式显示联机操作手册。

```bash
$ man command
```

### info

> 以超文本形式显示联机操作手册。

```bash
$ info command
```



### watch

> 监视命令，通过该命令可以实现实时跟踪对象的变化。`watch`可以帮你监测一个命令的运行结果，省得你一遍遍的手动运行。在Linux下，`watch`是周期性的执行下个程序，并全屏显示执行结果。
>
> ```shell
> $ watch [options]
> ```
>
> | Options            | Function                                                     |
> | ------------------ | ------------------------------------------------------------ |
> | `-n`/--interval    | watch缺省每2秒运行一下程序，可以用-n或-interval来指定间隔的时间。 |
> | `-d`/--differences | 用-d或--differences 选项watch 会高亮显示变化的区域。 而-d=cumulative选项会把变动过的地方(不管最近的那次有没有变动)都高亮显示出来。 |
> | `-t` /-no-title    | 关闭watch命令在顶部的时间间隔，即当前时间的输出。            |
> | `-h`/--help        | 查看帮助文档                                                 |





# Chapter3 实践经历

## 1. 查看系统配置

> 具体系统设备可通过系统设备配置文件进行查看，该目录位于 `/sys/devices/system/`，其中

### CPU

```bash
$ lscpu		# show  device info of CPU

```

> Fields Management for window 1:Def, whose current sort field is %CPU
>    Navigate with Up/Dn, Right selects for move then <Enter> or Left commits,
>    'd' or <Space> toggles display, 's' sets sort.  Use 'q' or <Esc> to end!


|Key      | Descritption   | Key     | Descritption  |  Key     | Descritption |
|---      | ---   |---      | ---   |---      | ---   |
| PID     | Process Id     | TIME    | CPU Time      |  RSan    | RES Anonymous|
| USER    | Effective Use  | SWAP    | Swapped Size  |  RSfd    | RES File-base|
| PR      | Priority       | CODE    | Code Size (Ki |  RSlk    | RES Locked (K|
| NI      | Nice Value     | DATA    | Data+Stack (K |  RSsh    | RES Shared (K|
| VIRT    | Virtual Image  | nMaj    | Major Page Fa |  CGNAME  | Control Group|
| RES     | Resident Size  | nMin    | Minor Page Fa |  NU      | Last Used NUM|
| SHR     | Shared Memory  | nDRT    | Dirty Pages C|||
| S       | Process Statu  | WCHAN   | Sleeping in F|||
| %CPU    | CPU Usage      | Flags   | Task Flags |||
| %MEM    | Memory Usage   | CGROUPS | Control Group|||
| TIME+   | CPU Time, hun  | SUPGIDS | Supp Groups I|||
| COMMAND | Command Name/Line | SUPGRPS | Supp Groups N|||


### GPU

> 

#### For NVIDIA

```SHELL
$ nvidia-smi
# watch -n nvidia-smi	# Show result of program periodically
```

其中各参数解释如下：

| 参数          | 说明                                                         |
| ------------- | ------------------------------------------------------------ |
| Fan           | N/A是风扇转速，从0到100%之间变动。有的设备不会返回转速，因为它不依赖风扇冷却而是通过其他外设保持低温。 |
| Temp          | 温度，单位摄氏度                                             |
| Perf          | 性能状态，从P0到P12，P0表示最大性能，P12表示状态最小性能     |
| Pwr           | 能耗                                                         |
| Persistence-M | 持续模式的状态，持续模式虽然耗能大，但是在新的GPU应用启动时，花费的时间更少， |
| Bus-Id        | GPU总线                                                      |
| domain        | :bus:device.function                                         |
| Disp.A        | Display Active，表示GPU的显示是否初始化                      |
| Memory Usage  | 显存使用率                                                   |
| Compute M     | 计算模式                                                     |



## 2. 内存管理

### 2.1 概述

> 在日常运维中，我们会发现主机内存使用告警，为什么Linux系统没运行多少程序，显示的可用内存这么少？其实Linux与Win的内存管理不同，会尽量缓存内存以提高读写性能，通常叫做Cache Memory。
>
> 有时候你会发现没有什么程序在运行，但是使用top或free命令看到可用内存free显示很少，我们可以使用`cat /proc/meminfo` 或`free -m`查看内存信息，还有一项 Cached Memory。

### 2.2 基本概念

> `Mem` 内存的使用信息
>
> `Swap` 交换空间的使用信息
>
> `total` 系统总的可用物理内存大小
>
> `used` 已被使用的物理内存大小
>
> `free` 还有多少物理内存可用
>
> `shared` 被共享使用的物理内存大小
>
> `buff/cache` 被 buffer 和 cache 使用的物理内存大小
>
> `available` 还可以被**应用程序**使用的物理内存大小

**free 与 available 的区别**
free 是真正尚未被使用的物理内存数量。
available 是应用程序认为可用内存数量，available = free + buffer + cache (注：只是大概的计算方法)

### 2.3 缓存机制介绍

> 在Linux系统中，为了提高文件系统性能，内核利用一部分物理内存分配出缓冲区，用于缓存系统操作和数据文件，当内核收到读写的请求时，内核先去缓存区找是否有请求的数据，有就直接返回，如果没有则通过驱动程序直接操作磁盘。对于内核来说，buffer 和 cache 其实都属于已经被使用的内存。但当应用程序申请内存时，如果 free 内存不够，内核就会回收 buffer 和 cache 的内存来满足应用程序的请求。这就是稍后要说明的 buffer 和 cache。
>
> **缓存机制优点**：减少系统调用次数，降低CPU上下文切换和磁盘访问频率。
>
> **CPU上下文切换：**CPU给每个进程一定的服务时间，当时间片用完后，内核从正在运行的进程中收回处理器，同时把进程当前运行状态保存下来，然后加载下一个任务，这个过程叫做上下文切换。实质上就是被终止运行进程与待运行进程的进程切换。

#### 缓存区分buffers和cached区别

内核在保证系统能正常使用物理内存和数据量读写情况下来分配缓冲区大小。
buffers用来缓存metadata及pages，可以理解为系统缓存，例如，vi打开一个文件。
cached是用来给文件做缓存，可以理解为数据块缓存，例如，dd if=/dev/zero of=/tmp/test count=1 bs=1G 测试写入一个文件，就会被缓存到缓冲区中，当下一次再执行这个测试命令时，写入速度会明显很快。

**具体解释：**

buffer和[cache](http://www.idcyunwei.org/post/162.html)是两个在计算机技术中被用滥的名词，放在不通语境下会有不同的意义。在Linux的内存管理中，这里的buffer指Linux内存的：Buffer cache。这里的cache指Linux内存中的：Page cache。翻译成中文可以叫做缓冲区缓存和页面缓存。在历史上，它们一个（buffer）被用来当成对io设备写的缓存，而另一个（cache）被用来当作对io设备的读缓存，这里的io设备，主要指的是块设备文件和文件系统上的普通文件。但是现在，它们的意义已经不一样了。在当前的内核中，page cache顾名思义就是针对内存页的缓存，说白了就是，如果有内存是以page进行分配管理的，都可以使用page cache作为其缓存来管理使用。当然，不是所有的内存都是以页（page）进行管理的，也有很多是针对块（block）进行管理的，这部分内存使用如果要用到cache功能，则都集中到buffer cache中来使用。（从这个角度出发，是不是buffer cache改名叫做block cache更好？）然而，也不是所有块（block）都有固定长度，系统上块的长度主要是根据所使用的块设备决定的，而页长度在X86上无论是32位还是64位都是4k。

**1、什么是page cache？**

Page cache主要用来作为文件系统上的文件数据的缓存来用，尤其是针对当进程对文件有read／write操作的时候。如果你仔细想想的话，作为可以映射文件到内存的系统调用：mmap是不是很自然的也应该用到page cache？在当前的系统实现里，page cache也被作为其它文件类型的缓存设备来用，所以事实上page cache也负责了大部分的块设备文件的缓存工作。

**2、什么是buffer cache？**

Buffer cache则主要是设计用来在系统对块设备进行读写的时候，对块进行数据缓存的系统来使用。这意味着某些对块的操作会使用buffer cache进行缓存，比如我们在格式化文件系统的时候。一般情况下两个缓存系统是一起配合使用的，比如当我们对一个文件进行写操作的时候，page cache的内容会被改变，而buffer cache则可以用来将page标记为不同的缓冲区，并记录是哪一个缓冲区被修改了。这样，内核在后续执行脏数据的回写（writeback）时，就不用将整个page写回，而只需要写回修改的部分即可。

### 2.4 Swap用途

Swap意思是交换分区，通常我们说的虚拟内存，是从硬盘中划分出的一个分区。当物理内存不够用的时候，内核就会释放缓存区（buffers/cache）里一些长时间不用的程序，然后将这些程序临时放到Swap中，也就是说如果物理内存和缓存区内存不够用的时候，才会用到Swap。
swap清理：
swapoff -a && swapon -a
**注意：**这样清理有个前提条件，空闲的内存必须比已经使用的swap空间大

### 2.5 释放缓存区内存的方法


1、清理pagecache（页面缓存）
```bash
$ echo 1> /proc/sys/vm/drop_caches 
# 或者 sysctl -w vm.drop_caches=1
```
2、清理dentries（目录缓存）和inodes

```bash
$ echo 2> /proc/sys/vm/drop_caches 
# 或者 sysctl -w vm.drop_caches=2
```
3、清理pagecache、dentries和inodes

```bash
$ echo 3> /proc/sys/vm/drop_caches 
# 或者 sysctl -w vm.drop_caches=3
```

这个文件可以设置的值分别为1、2、3。它们所表示的含义为：

```bash
$ echo 1> /proc/sys/vm/drop_caches		# 表示清除pagecache。
$ echo 2> /proc/sys/vm/drop_caches		# 表示清除回收slab分配器中的对象（包括目录项缓存和inode缓存）。slab分配器是内核中管理内存的一种机制，其中很多缓存数据实现都是用的pagecache。
$ echo 3> /proc/sys/vm/drop_caches		# 表示清除pagecache和slab分配器中的缓存对象。　
```

上面三种方式都是临时释放缓存的方法，要想永久释放缓存，需要在/etc/sysctl.conf文件中配置：vm.drop_caches=1/2/3，然后sysctl -p生效即可！
另外，可以使用sync命令来清理文件系统缓存，还会清理僵尸(zombie)对象和它们占用的内存。

```bash
$ sync　　
```

### 2.6 注意事项　　

关于清除缓存的操作在大多数情况下都不会对系统造成伤害，只会有助于释放不用的内存。
但是如果在执行这些操作时正在写数据，那么实际上在数据到达磁盘之前就将它从文件缓存中清除掉了，这可能会造成很不好的影响。那么如果避免这种事情发生呢？
因此，这里不得不提一下/proc/sys/vm/vfs_cache_pressure这个文件，告诉内核，当清理inoe/dentry缓存时应该用什么样的优先级。


vfs_cache_pressure=100 这个是默认值，内核会尝试重新声明dentries和inodes，并采用一种相对于页面缓存和交换缓存比较”合理”的比例。
减少vfs_cache_pressure的值，会导致内核倾向于保留dentry和inode缓存。
增加vfs_cache_pressure的值，（即超过100时），则会导致内核倾向于重新声明dentries和inodes

总之，vfs_cache_pressure的值：
小于100的值不会导致缓存的大量减少
超过100的值则会告诉内核你希望以高优先级来清理缓存。
其实无论vfs_cache_pressure的值采用什么值，内核清理缓存的速度都是比较低的。
如果将此值设置为10000，系统将会将缓存减少到一个合理的水平。


释放内存前先使用sync命令做同步，以确保文件系统的完整性，将所有未写的系统缓冲区写到磁盘中，包含已修改的 i-node、已延迟的块 I/O 和读写映射文件。否则在释放缓存的过程中，可能会丢失未保存的文件。

/proc是一个虚拟文件系统，可以通过对它的读写操作作为与kernel实体间进行通信的一种手段。也就是说可以通过修改/proc中的文件，来对当前kernel的行为做出调整。也就是说我们可以通过调整/proc/sys/vm/drop_caches来释放内存。

drop_caches的值可以是0-3之间的数字，代表不同的含义：

> 0：不释放（系统默认值）
>
> 1：释放页缓存
>
> 2：释放dentries和inodes
>
> 3：释放所有缓存



## 3. 文件管理

> 当Windows非正常关闭时，windows系统会对其磁盘内存锁定保护，导致Linux系统无法写入修改windows系统分区盘。





# Chapter4 基于计算机网络的命令

## 1. 路由跟踪

### PING

> 分组网间探测 PING(Packet InterNet Groper)
>
> 发送 ICMP 报文检测终点可达性

### traceroute

------

互联网是由网关连接在一起的大型复杂的网络硬件集合。跟踪数据包遵循的路由（或找到丢弃数据包的网关）可能很困难。 traceroute 命令利用 IP 协议的“生存时间”字段，并尝试从每个网关到某个主机的路径引发 ICMP TIME_EXCEEDED 响应。

![img](/home/hedge/Tools/typora_images/traceroute.jpg)

唯一必需的参数是目标主机名或 IP 地址。默认的探测数据报长度为 40 - 60 字节，但是可以通过在目标主机名之后指定数据包大小（以字节为单位）来增加长度。

traceroute 尝试通过启动具有较小 ttl（生存时间）的探测数据包，然后侦听来自网关的 `ICMP` “超过时间” 答复来跟踪 IP 数据包将遵循的路由到某些 Internet 主机的路由。它以 1 的 ttl 开始其探测，并将其增加 1，直到获得 ICMP “端口不可达”（或 TCP 重置），这意味着我们到达了“主机”，或者达到了最大值（默认为 30 跳）...在每个 ttl 设置下发送三个探针（默认情况下），并打印一行以显示 ttl，网关地址和每个探针的往返时间。要求时，地址后可以有其他信息。如果探测答案来自不同的网关，则将打印每个响应系统的地址。如果在 5.0 秒内（默认）没有响应，则为该探针打印一个 “*”（星号）。

#### traceroute 命令语法：

------

```
traceroute [-46dFITUnreAV] [-f first_ttl] [-g gate,...] [-i device] 
           [-m max_ttl] [-p port] [-s src_addr] [-q nqueries] 
           [-N squeries] [-t tos] [-l flow_label] [-w waittime] 
           [-z sendwait] [-UL] [-D] [-P proto] [--sport=port] [-M method] 
           [-O mod_options] [--mtu] [--back] host [packet_len] 
```

#### traceroute 命令选项：

------

```
-d：使用Socket层级的排错功能；
-f<存活数值>：设置第一个检测数据包的存活数值TTL的大小；
-F：设置勿离断位；
-g<网关>：设置来源路由网关，最多可设置8个；
-i<网络界面>：使用指定的网络界面送出数据包；
-I：使用ICMP回应取代UDP资料信息；
-m<存活数值>：设置检测数据包的最大存活数值TTL的大小；
-n：直接使用IP地址而非主机名称；
-p<通信端口>：设置UDP传输协议的通信端口；
-r：忽略普通的Routing Table，直接将数据包送到远端主机上。
-s<来源地址>：设置本地主机送出数据包的IP地址；
-t<服务类型>：设置检测数据包的TOS数值；
-v：详细显示指令的执行过程；
-w<超时秒数>：设置等待远端主机回报的时间；
-x：开启或关闭数据包的正确性检验。
```

#### traceroute 命令参数：

------

```
主机：指定目的主机IP地址或主机名。
```

记录按序列号从 1 开始，每个纪录就是一跳 ，每跳表示一个网关，我们看到每行有三个时间，单位是 `ms`，其实就是 -q 的默认参数。探测数据包向每个网关发送三个数据包后，网关响应后返回的时间；如果用 `traceroute -q 4 www.58.com`，表示向每个网关发送 4 个数据包。

有时我们 traceroute 一台主机时，会看到有一些行是以星号表示的。出现这样的情况，可能是防火墙封掉了 ICMP 的返回信息，所以我们得不到什么相关的数据包返回数据。

有时我们在某一网关处延时比较长，有可能是某台网关比较阻塞，也可能是物理设备本身的原因。当然如果某台 DNS 出现问题时，不能解析主机名、域名时，也会有延时长的现象；您可以加 -n 参数来避免 DNS 解析，以 IP 格式输出数据。

如果在局域网中的不同网段之间，我们可以通过 traceroute 来排查问题所在，是主机的问题还是网关的问题。如果我们通过远程来访问某台服务器遇到问题时，我们用到 traceroute 追踪数据包所经过的网关，提交 IDC 服务商，也有助于解决问题；但目前看来在国内解决这样的问题是比较困难的，就是我们发现问题所在，IDC服务商也不可能帮助我们解决。



## 2. NIC

### iwconfig

> iwconfig是 Linux 用于对无线网卡的大部分参数进行配置的工具，早期的操作系统通过 ipconfig 实现。

```bash
$ iwconfig [interface]
            interface essid {NNN|any|on|off}
            interface mode {managed|ad-hoc|master|...}
            interface freq N.NNN[k|M|G]
            interface channel N
            interface bit {N[k|M|G]|auto|fixed}
            interface rate {N[k|M|G]|auto|fixed}
            interface enc {NNNN-NNNN|off}
            interface key {NNNN-NNNN|off}
            interface power {period N|timeout N|saving N|off}
            interface nickname NNN
            interface nwid {NN|on|off}
            interface ap {N|off|auto}
            interface txpower {NmW|NdBm|off|auto}
            interface sens N
            interface retry {limit N|lifetime N}
            interface rts {N|auto|fixed|off}
            interface frag {N|auto|fixed|off}
            interface modulation {11g|11a|CCK|OFDMg|...}
            interface commit
```

#### 参数说明

> **essid**：设置无线网卡的ESSID(Extension Service Set ID)。通过ESSID来区分不同的无线网络，正常情况下只有相同ESSID的无线站点才可以互相通讯，除非想监听无线网络。其后的参数为双引号括起的ESSID字符串，或者是any/on/off，如果ESSID字符串中包含any/no/off，则需要在前面加"--"。

```shell
$ iwconfig eth0 essid any          					# 允许任何ESSID，也就是混杂模式

$ iwconfig eth0 essid "My Network"     	# 设置ESSID为"My Network"

$ iwconfig eth0 essid -- "ANY"       			# 设置ESSID为"ANY"
```

> **nwid:** Network ID，只用于pre-802.11的无线网卡，802.11网卡利用ESSID和AP的MAC地址来替换nwid，现在基本上不用设置。

````shell
$ iwconfig eth0 nwid AB34

$ iwconfig eth0 nwid off 
````

> **nick:** Nickname，一些网卡需要设置该参数，但是802.11协议栈、MAC都没有用到该参数，一般也不用设置。

```shell 
$ iwconfig eth0 nickname "My Linux Node"
```

> **mode：**设置无线网卡的工作模式，可以是
>
> Ad-hoc：不带AP的点对点无线网络
>
> Managed：通过多个AP组成的网络，无线设备可以在这个网络中漫游
>
> Master：设置该无线网卡为一个AP
>
> Repeater：设置为无线网络中继设备，可以转发网络包
>
> Secondary：设置为备份的AP/Repeater
>
> Monitor：监听模式
>
> Auto：由无线网卡自动选择工作模式

```shell
$ iwconfig eth0 mode Managed

$ iwconfig eth0 mode Ad-Hoc
```

> **freq/channel：**设置无线网卡的工作频率或者频道，小于1000的参数被认为是频道，大于10000的参数被认为是频率。频率单位为Hz，可以在数字后面附带k, M, G来改变数量级，比如2.4G。频道从1开始。使用lwlist工具可以查看无线网卡支持的频率和频道。参数off/auto指示无线网络自动挑选频率。
>
> 注意：如果是Managed模式，AP会指示无线网卡的工作频率，因此该设置的参数会被忽略。Ad-hoc模式下只使用该设定的频率初始无线网络，如果加入已经存在的Ad-hoc网络则会忽略该设置的频率参数。

```shell
$ iwconfig eth0 freq 2422000000

$ iwconfig eth0 freq 2.422G

$ iwconfig eth0 channel 3

$ iwconfig eth0 channel auto                                                                                                                                         
```

> **ap：**连接到指定的AP或者无线网络，后面的参数可以是AP的MAC地址，也可以是iwlist scan出来的标识符。如果是Ad-hoc，则连接到一个已经存在的Ad-hoc网络。使用off参数让无线网卡不改变当前已连接的AP下进入自动模式。any/auto参数，无线网卡自动选择最好的AP。
>
> 注意：如果无线信号低到一定程度，无线网络会进入自动选择AP模式。

```shell
$ iwconfig eth0 ap 00:60:1D:01:23:45

$ iwconfig eth0 ap any

$ iwconfig eth0 ap off
```

> **rate/bit：**如果无线网卡支持多速率，则可以通过该命令设置工作的速率。小于1000的参数由具体的无线网卡驱动定义，一般是传输速率的索引值，大于1000的为速率，单位bps，可以在数字后面附带k, M, G来指定数量级。auto参数让无线网卡自动选择速率。fixed参数让无线网卡不使用自动速率模式。

```shell
$ iwconfig eth0 rate 11M

$ iwconfig eth0 rate auto

$ iwconfig eth0 rate 5.5M auto  //自动选择5.5M以下的速率
```

> **txpower：**如果无线网卡支持多发射功率设定，则使用该参数设定发射，单位为dBm，如果指定为W（毫瓦），只转换公式为：
>
> dBm=30+log(W)。参数on/off可以打开和关闭发射单元，auto和fixed指定无线是否自动选择发射功率。

```shell
$ iwconfig eth0 txpower 15

$ iwconfig eth0 txpower 30mW

$ wconfig eth0 txpower auto

$ iwconfig eth0 txpower off  
```

> **sens：**设置接收灵敏度的下限，在该下限之下，无线网卡认为该无线网络信号太差，不同的网卡会采取不同的措施，一些现代的无线网卡会自动选择新的AP。正的参数为raw data，直接传给无线网卡驱动处理，一般认为是百分比。负值表示dBm值。

```shell
$ iwconfig eth0 sens -80

$ iwconfig eth0 sens 2

```

> **retry：**设置无线网卡的重传机制。limit ‘value’ 指定最大重传次数；lifetime ‘value’指定最长重试时间，单位为秒，可以附带m和u来指定单位为毫秒和微秒。如果无线网卡支持自动模式，则在limit和lifetime之前还可以附加min和max来指定上下限值。

```shell
$ iwconfig eth0 retry 16

$ iwconfig eth0 retry lifetime 300m

$ iwconfig eth0 retry min limit 8
```

> **rts：**指定RTS/CTS握手方式，使用RTS/CTS握手会增加额外开销，但如果无线网络中有隐藏无线节点或者有很多无线节点时可以提高性能。后面的参数指定一个使用该机制的最小包的大小，如果该值等于最大包大小，则相当于禁止使用该机制。可以使用 auto/off/fixed 参数。

```shell
$ iwconfig eth0 rts 250

$ iwconfig eth0 rts off
```
​    

> **frag：**设置发送数据包的分片大小。设置分片会增加额外开销，但在噪声环境下可以提高数据包的到达率。一般情况下该参数小于最大包大小，有些支持Burst模式的无线网卡可以设置大于最大包大小的值来允许Burst模式。还可以使用auto/fixed/off参数。

```shell
$ iwconfig eth0 frag 512

$ iwconfig eth0 frag off   
```

> **key/enc[ryption]：**设置无线网卡使用的加密密钥，此处为设置WEP模式的加密key，如果要使用WPA，需要wpa_supplicant工具包。密钥参数可以是 XXXX-XXXX-XXXX-XXXX 或者 XXXXXXXX 格式的十六进制数值，也可以是s:xxxxxx的ASCII字符。如果在密钥参数之前加了[index]，则只是设置该索引值对应的密钥，并不改变当前的密钥。直接指定[index]值可以设置当前使用哪一个密钥。指定on/off可以控制是否使用加密模式。open/restricted指定加密模式，取决于不同的无线网卡，大多数无线网卡的open模式不使用加密且允许接收没有加密的数据包，restricted模式使用加密。可以使用多个key参数，但只有最后一个生效。WEP密钥可以是40bit，用10个十六进制数字或者5个ASCII字符表示，也可以是128bit，用26个十六进制数字或者13个ASCII字符表示。

```shell
$ iwconfig eth0 key 0123-4567-89

$ iwconfig eth0 key [3] 0123-4567-89

$ iwconfig eth0 key s:password [2]

$ iwconfig eth0 key [2]

$ iwconfig eth0 key open

$ iwconfig eth0 key off

$ iwconfig eth0 key restricted [3] 0123456789

$ iwconfig eth0 key 01-23 key 45-67 [4] key [4]
```

> **power：**设置无线网卡的电源管理模式。period ‘value’ 指定唤醒的周期，timeout ‘value’指定进入休眠的等待时间，这两个参数之前可以加min和max修饰，这些值的单位为秒，可以附加m和u来指定毫秒和微秒。off/on参数指定是否允许电源管理，all/unicast/multicast指定允许唤醒的数据包类型。

```shell
$ iwconfig eth0 power period 2

$ iwconfig eth0 power 500m unicast

$ iwconfig eth0 power timeout 300u all

$ iwconfig eth0 power off

$ iwconfig eth0 power min period 2 power max period 4
```

> **commit：**提交所有的参数修改给无线网卡驱动。有些无线网卡驱动会先缓存无线网卡参数修，使用这个命令来让无线网卡的参数修改生效。不过一般不需要使用该命令，因为无线网卡驱动最终都会是参数的修改生效，一般在debug时会用到。为了方便配置，可以把配置写到 /etc/network/interfaces中，这样以后就不用反复配置了。
```
auto lo

iface lo inet loopback



auto eth1

iface eth1 inet static

address 192.168.1.3

netmask 255.255.255.0

gateway 192.168.1.1

echo nameserver 192.168.1.1>/etc/resolv.conf

pre-up /sbin/iwconfig eth1 essid "LW HOME LINK"

pre-up /sbin/iwconfig eth1 key s:liwei

 

auto usb0

iface usb0 inet static

address 192.168.0.200

netmask 255.255.255.0

 

auto dsl-provider

iface dsl-provider inet ppp

pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

provider dsl-provider
```



### ip

> 查看当前 IP，若为内网则为内网 IP。

```bash
Usage:	 ip [ OPTIONS ] OBJECT { COMMAND | help }
       			ip [ -force ] -batch filename
where  
OBJECT := { address | addrlabel | amt | fou | help | ila | ioam | l2tp |
                   link | macsec | maddress | monitor | mptcp | mroute | mrule |
                   neighbor | neighbour | netconf | netns | nexthop | ntable |
                   ntbl | route | rule | sr | tap | tcpmetrics |
                   token | tunnel | tuntap | vrf | xfrm }
OPTIONS := { -V[ersion] | -s[tatistics] | -d[etails] | -r[esolve] |
                    -h[uman-readable] | -iec | -j[son] | -p[retty] |
                    -f[amily] { inet | inet6 | mpls | bridge | link } |
                    -4 | -6 | -M | -B | -0 |
                    -l[oops] { maximum-addr-flush-attempts } | -br[ief] |
                    -o[neline] | -t[imestamp] | -ts[hort] | -b[atch] [filename] |
                    -rc[vbuf] [size] | -n[etns] name | -N[umeric] | -a[ll] |
                    -c[olor]}
```

> 查看公网 IP，借助网站实现，进一步用法也可参考原网站

```shell
$ curl ifconfig.me
# 或以下命令均可，任意该类型网站均可
$ curl sipv4.com
```

#### Command Line Interface

| Command                      | Answer                                                       |
| ---------------------------- | ------------------------------------------------------------ |
| $ curl ifconfig.me           | 58.249.112.19                                                |
| $ curl ifconfig.me/ip        | 58.249.112.19                                                |
| $ curl ifconfig.me/ua        | Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.4951.64 Safari/537.36 |
| $ curl ifconfig.me/lang      | zh-CN,zh;q=0.9                                               |
| $ curl ifconfig.me/encoding  |                                                              |
| $ curl ifconfig.me/mime      | text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9 |
| $ curl ifconfig.me/charset   |                                                              |
| $ curl ifconfig.me/forwarded | 58.249.112.19, 34.117.59.81,35.191.2.85                      |
| $ curl ifconfig.me/all       | ip_addr: 58.249.112.19 remote_host: unavailable <br />user_agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.4951.64 Safari/537.36 <br />port: 33336 <br />language: zh-CN,zh;q=0.9 <br />referer: https://blog.csdn.net/MoSee/article/details/77489677 <br />connection: keep_alive: <br />method: GET <br />encoding: mime: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9 <br />charset: via: 1.1 google forwarded: 58.249.112.19, 34.117.59.81,35.191.2.85 |
| $ curl ifconfig.me/all.json  | {"ip_addr":"58.249.112.19","remote_host":"unavailable","user_agent":"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.4951.64 Safari/537.36","port":33336,"language":"zh-CN,zh;q=0.9","referer":"https://blog.csdn.net/MoSee/article/details/77489677","method":"GET","mime":"text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9","via":"1.1 google","forwarded":"58.249.112.19, 34.117.59.81,35.191.2.85"} |



## 3. PORT

### 3.1 基本命令

> `lsof` 命令用于查看进程开打的文件，打开文件的进程，进程打开的端口(TCP、UDP)。找回/恢复删除的文件。
>
> `ss`(Socket statistics) 命令用于 ArchLinux 等系统查看端口状态，相比于 Ubuntu 等系统使用的 `netstat`，能够提供更多有关端口尤其是套接字的详细情况。

#### 参考

> 1. [Linux 命令神器：lsof 入门](https://linux.cn/article-4099-1.html)
> 2. [linux lsof命令详解](https://www.itbiancheng.com/article/5481.html)

```shell
$ ss
$ lsof -nP -iTCP -sTCP:LISTEN		# 侦听所有TCP端口列表
$ sudo lsof -nP -iTCP:<PORT> -sTCP:LISTEN		# 侦听指定端口
```

#### 帮助信息

```
$ ss -h
-h, --help this message 帮助信息
-V, --version output version information 输出版本信息
-n, --numeric don't resolve service names 不解析服务名称
-r, --resolve resolve host names 解析主机名
-a, --all display all sockets 显示所有套接字
-l, --listening display listening sockets 显示侦听套接字
-o, --options show timer information 显示计时器信息
-e, --extended show detailed socket information 显示详细的套接字信息
-m, --memory show socket memory usage 显示套接字内存使用量
-p, --processes show process using socket 显示使用socket的进程信息
-i, --info show internal TCP information 显示内部TCP信息
--tipcinfo show internal tipc socket information 显示内部tipc套接字信息
-s, --summary show socket usage summary show socket使用摘要
--tos show tos and priority information 显示tos和优先级信息
-b, --bpf show bpf filter socket information 显示bpf过滤器套接字信息
-E, --events continually display sockets as they are destroyed 在它们被摧毁时不断显示套接字
-Z, --context display process SELinux security contexts 显示进程SELinux安全上下文
-z, --contexts display process and socket SELinux security contexts 显示进程和套接字SELinux安全上下文
-N, --net switch to the specified network namespace name 切换到指定的网络命名空间名称
 
-4, --ipv4 display only IP version 4 sockets 只显示ipv4的套接字；
-6, --ipv6 display only IP version 6 sockets 只显示ipv6的套接字；
-0, --packet display PACKET sockets 显示PACKET套接字
-t, --tcp display only TCP sockets 仅显示TCP套接字
-S, --sctp display only SCTP sockets 仅显示SCTP套接字
-u, --udp display only UDP sockets 仅显示UDP套接字
-d, --dccp display only DCCP sockets 仅显示DCCP套接字
-w, --raw display only RAW sockets 仅显示RAW套接字
-x, --unix display only Unix domain sockets 仅显示Unix域套接字
--tipc display only TIPC sockets 仅显示TIPC套接字
--vsock display only vsock sockets 仅显示vsock套接字
-f, --family=FAMILY display sockets of type FAMILY 显示FAMILY类型的套接字
FAMILY := {inet|inet6|link|unix|netlink|vsock|tipc|help}
 
-K, --kill forcibly close sockets, display what was closed 强行关闭套接字，显示已关闭的内容
-H, --no-header Suppress header line 抑制标题行
 
-A, --query=QUERY, --socket=QUERY QUERY := {all|inet|tcp|udp|raw|unix|unix_dgram|unix_stream|unix_seqpacket|packet|netlink|vsock_tipc}[,QUERY]
 
-D, --diag=FILE Dump raw information about TCP sockets to FILE 将有关TCP套接字的原始信息转储到FILE
-F, --filter=FILE read filter information from FILE 从FILE中读取过滤器信息
FILTER := [ state STATE-FILTER ] [ EXPRESSION ]
STATE-FILTER := {all|connected|synchronized|bucket|big|TCP-STATES}
TCP-STATES := {established|syn-sent|syn-recv|fin-wait-{1,2}|time-wait|closed|close-wait|last-ack|listening|closing}
connected := {established|syn-sent|syn-recv|fin-wait-{1,2}|time-wait|close-wait|last-ack|closing}
synchronized := {established|syn-recv|fin-wait-{1,2}|time-wait|close-wait|last-ack|closing}
bucket := {syn-recv|time-wait}
big := {established|syn-sent|fin-wait-{1,2}|closed|close-wait|last-ack|listening|closing}
```

### 3.2 选项分类说明

```
这2个选项(-n, -r)不能同时使用
-n, --numeric don't resolve service names 不解析服务名称
-r, --resolve resolve host names 解析主机名

统计摘要
-s, --summary show socket usage summary show socket使用摘要

显示全部
-a, --all display all sockets 显示所有套接字

仅显示部分
-l, --listening display listening sockets 显示侦听套接字
-4, --ipv4 display only IP version 4 sockets 只显示ipv4的套接字；
-6, --ipv6 display only IP version 6 sockets 只显示ipv6的套接字；
-0, --packet display PACKET sockets 显示PACKET套接字
-t, --tcp display only TCP sockets 仅显示TCP套接字
-S, --sctp display only SCTP sockets 仅显示SCTP套接字
-u, --udp display only UDP sockets 仅显示UDP套接字
-d, --dccp display only DCCP sockets 仅显示DCCP套接字
-w, --raw display only RAW sockets 仅显示RAW套接字
-x, --unix display only Unix domain sockets 仅显示Unix域套接字

其他更多信息
-p, --processes show process using socket 显示使用socket的进程信息
-o, --options show timer information 显示计时器信息
-e, --extended show detailed socket information 显示详细的套接字信息
-m, --memory show socket memory usage 显示套接字内存使用量
-i, --info show internal TCP information 显示内部TCP信息
```

### 3.3 过滤选项 family

```
-f, --family=FAMILY display sockets of type FAMILY 显示FAMILY类型的套接字
FAMILY := {inet|inet6|link|unix|netlink|vsock|tipc|help} 
```

### 3.4 过滤选项 state

```
state : {all|connected|synchronized|bucket|big|TCP-STATES}
TCP-STATES := {established|syn-sent|syn-recv|fin-wait-{1,2}|time-wait|closed|close-wait|last-ack|listening|closing}
connected := {established|syn-sent|syn-recv|fin-wait-{1,2}|time-wait|close-wait|last-ack|closing}
synchronized := {established|syn-recv|fin-wait-{1,2}|time-wait|close-wait|last-ack|closing}
bucket := {syn-recv|time-wait}
big := {established|syn-sent|fin-wait-{1,2}|closed|close-wait|last-ack|listening|closing}
```

### 3.5 状态之间的关系

图1:客户端和服务器建立连接的握手过程原理图

![img](/home/hedge/Tools/typora_images/1085375-20190504233947953-860269922.png) 

图2:TCP状态转移图

![img](/home/hedge/Tools/typora_images/1085375-20190504234001954-319688499.png) 

图3:关闭部分的状态转移图

![img](/home/hedge/Tools/typora_images/1085375-20190504234011790-1171109389.png)



## 4. HTTP

ArchLinux 使用 `curl` 命令模拟 HTTP 请求。具体用法如下：

```shell
$ curl [option] [URL]
```

### 参考资料

> 1. [Archwiki](https://wiki.archlinux.org/title/CURL#Usage)
> 2. [Archwiki Manual](https://man.archlinux.org/man/curl.1)
> 3. [CURL EVERYTHING](https://everything.curl.dev/)(PDF in local)





# 待整理垃圾

```
系统

# uname -a               # 查看内核/操作系统/CPU信息
# head -n 1 /etc/issue   # 查看操作系统版本
# cat /proc/cpuinfo      # 查看CPU信息
# hostname               # 查看计算机名
# lspci -tv              # 列出所有PCI设备
# lsusb -tv              # 列出所有USB设备
# lsmod                  # 列出加载的内核模块
# env                    # 查看环境变量

资源

# free -m                # 查看内存使用量和交换区使用量
# df -h                  # 查看各分区使用情况
# du -sh <目录名>        # 查看指定目录的大小
# grep MemTotal /proc/meminfo   # 查看内存总量
# grep MemFree /proc/meminfo    # 查看空闲内存量
# uptime                 # 查看系统运行时间、用户数、负载
# cat /proc/loadavg      # 查看系统负载

磁盘和分区

# mount | column -t      # 查看挂接的分区状态
# fdisk -l               # 查看所有分区
# swapon -s              # 查看所有交换分区
# hdparm -i /dev/hda     # 查看磁盘参数(仅适用于IDE设备)
# dmesg | grep IDE       # 查看启动时IDE设备检测状况

网络

# iptables -L            # 查看防火墙设置

进程

# ps -ef                 # 查看所有进程
# top                    # 实时显示进程状态

用户

# w                      # 查看活动用户
# id <用户名>            # 查看指定用户信息
# last                   # 查看用户登录日志
# cut -d: -f1 /etc/passwd   # 查看系统所有用户
# cut -d: -f1 /etc/group    # 查看系统所有组
# crontab -l             # 查看当前用户的计划任务

常用命令整理如下：
查看主板的序列号: dmidecode | grep -i ’serial number’

用硬件检测程序kuduz探测新硬件：service kudzu start ( or restart)

查看CPU信息：cat /proc/cpuinfo [dmesg | grep -i 'cpu'][dmidecode -t processor]

查看内存信息：cat /proc/meminfo [free -m][vmstat]

查看板卡信息：cat /proc/pci

查看显卡/声卡信息：lspci |grep -i ‘VGA’[dmesg | grep -i 'VGA']

查看网卡信息：dmesg | grep -i ‘eth’[cat /etc/sysconfig/hwconf | grep -i eth][lspci | grep -i 'eth']

查看PCI信息：lspci (相比cat /proc/pci更直观）

查看USB设备：cat /proc/bus/usb/devices

查看键盘和鼠标:cat /proc/bus/input/devices

查看系统硬盘信息和使用情况：fdisk & disk – l & df

查看各设备的中断请求(IRQ):cat /proc/interrupts

查看及启动系统的32位或64位内核模式：isalist –v [isainfo –v][isainfo –b]

dmidecode查看硬件信息，包括bios、cpu、内存等信息

测定当前的显示器刷新频率：/usr/sbin/ffbconfig –rev \?

查看系统配置：/usr/platform/sun4u/sbin/prtdiag –v

查看当前系统中已经应用的补丁：showrev –p

显示当前的运行级别：who –rH

查看当前的bind版本信息：nslookup –class=chaos –q=txt version.bind

dmesg | more 查看硬件信息
lspci 显示外设信息, 如usb，网卡等信息
prtvtoc /dev/rdsk/c0t0d0s 查看磁盘的几何参数和分区信息
df –F ufs –o i 显示已经使用和未使用的i-node数目

对于“/proc”中文件可使用文件查看命令浏览其内容，文件中包含系统特定信息：
Cpuinfo 主机CPU信息
Dma 主机DMA通道信息
Filesystems 文件系统信息
Interrupts 主机中断信息
Ioprots 主机I/O端口号信息
Meninfo 主机内存信息
Version Linux内存版本信息

备注： proc – process information pseudo-filesystem 进程信息伪装文件系统
```

