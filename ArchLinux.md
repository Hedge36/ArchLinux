# Chapter1 基本命令

## 1. 基本操作

### 1.1 路径操作





### 1.2 文件操作

#### Show infomation of dir

> list all of files and dirs with file in white and dir in blue. Show more info with params.

``` bash
ls [Params]
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
touch filenames [Params]
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
rm dirnames [Params]
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
cp source_path target_path [Params]
```

Copy files(That means source_path can be multiple files)  from source to target. And add a symbol“/” to copy a directory. 

> **Tip:** Use symbol “*” to Represents any character, like “file\*” means all files with a name beginning with “file”.

##### Param

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
mv source_path target_path [Params]
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
mkdir dirnames [Params]
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
rmdir dirnames [Params]
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

![03-01-02.png](/home/hedge/Typora/Temp-image/03-01-02.png)

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

#### Concate file

> `Cat` can just read file with just one source_file, or overwrite /  append characters of source to target, even concate data several file to a new.

```bash
cat source_file [op  target_file]
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



#### More file

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

#### less file

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

#### **Find file**

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



#### **Grep file**

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

#### sed file

> Operate file lines according to condition.

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

#### awk file

## 3. 短命令

> Modify the configure file of zsh.

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

其中tar命令参数分别如下

| 参数 | 含义     |
| ---- | -------- |
| z    | 压缩格式 |
| x    | 解压     |
| v    | 详细信息 |
| f    | 文件     |

其中z参数所在对应格式flag为：

| flag | 说明  |
| ---- | ----- |
| z    | gz    |
| j    | bzip2 |
| J    | xz    |
| Z    | Z     |

**事实上, 从1.15版本开始tar就可以自动识别压缩的格式,故不需人为区分压缩格式就能正确解压**

```bash 
$ tar -xvf <filename_tar.gz>
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
>

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

### pacman

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

### yay

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

###  deb

> **注意debtap需要安装！**
>
> **实际上，deb并不是一个包管理，而是一个纯粹的安装工具！**

更新debtap数据库

```bash
$ sudo debtap -u
```

使用debtap转换deb包

```bash
$ debtap xxx.deb
```

安装

```bash
$ sudo pacman -U xxx.pkg
```

删除

```bash
$ 
```





## 2. 进程管理

### 2.1 进程查看命令

> 查看进程信息的命令是ps(progress status)命令。该命令可查看记录在进程PCB中的所有信息，默认情况下。该命令只显示本终端上运行的所有进程。

```bash
$ ps [option]
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





## 3. 用户管理

### 1. 用户日志

有关用户登录的信息记录在 utmp(/var/run/utmp), wtmp(/var/log/wtmp), btmp(/var/log/btmp) 和 lastlog(/var/log/lastlog) 等文件中。

> who、w 和 users 等命令通过 utmp(/var/run/utmp) 文件查询当前登录用户的信息。
>
> last 和 ac 命令通过 wtmp(/var/log/wtmp) 文件查询当前与过去登录系统的用户的信息。
>
> lastb 命令通过 btmp(/var/log/btmp) 文件查询所有登录系统失败的用户的信息。
>
> lastlog 命令通过 lastlog(/var/log/lastlog) 文件查询用户最后一次登录的信息。

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

useradd 命令的用法是：`useradd 用户名`。添加用户时，还有一些常用的选项：

**选项名含义作用**-uUID手动为用户设置组 ID-ddirectory，家目录手工指定用户的家目录-ccomment，用户说明手工指定用户的说明，如果有空格，需要将说明文字用双引号括起来-ggroup，组名手工指定用户的初始组-Ggroup，组名手工指定用户的附加组，如果有多个附加组，用空格隔开-sshell，命令解释器手工指定用户的登录 shell，默认是 /bin/bash

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

![img](/home/hedge/Typora/Temp-image/v2-417bad4a3675b4eadfc2bcda166a7114_r.jpg)

这里显示的信息其实就是 `/etc/shadow` 文件中用户 supermouse 的密码信息。

#### -l 锁定用户，-u 解锁用户

不难猜到，-l 是 lock 的意思，而 -u 就是 unclock。使用方式：

```powershell
passwd -l supermouse # 锁定用户
passwd -u supermouse # 解锁用户
```

锁定用户时，Linux 执行的操作其实就是在 shadow 文件中，该用户的密码前面加了两个感叹号。如图所示：

![img](/home/hedge/Typora/Temp-image/v2-59a9a422769cc49a083839c6c1ca72c6_r.jpg)

![img](/home/hedge/Typora/Temp-image/v2-e1d9c65332ad9106de0b95c6b1eff398_r.jpg)

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

![img](/home/hedge/Typora/Temp-image/v2-e3cbcea5980741777b6ee34e5f15e20e_r.jpg)

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

![img](/home/hedge/Typora/Temp-image/v2-1ecfda0a977006fb27e1cf35309fd8ce_r.jpg)

### 8. 用户切换命令

su 是 switch user 的简写，su 命令的一般用法是：`su - 用户名`，**注意：中间的那个短线不能省略，而且短线两侧有空格。**

其实如果不加中间的那个短线，该命令也能正常执行，只不过不是完全地切换用户，在执行某些命令的时候会报错，我们来看一下加短线与不加短线的区别。

这是不加短线的：

![img](/home/hedge/Typora/Temp-image/v2-4b264f2b822b0623134fe5701a8e2c9e_720w.jpg)

没有报错，似乎已经切换到 root 用户了，但是我们来看一下此时的环境变量：

![img](/home/hedge/Typora/Temp-image/v2-30bb01bcbec4f50e39e657d17aa22b55_r.jpg)

看图中圈出来的跟当前用户相关的部分，包括当前登录的用户名、家目录、用户邮箱等，还都是原来的 supermouse，而不是 root。

再来看加上短线的效果：

![img](/home/hedge/Typora/Temp-image/v2-e871c8cfb25408c3e845034dfae49dbd_720w.jpg)

看一下环境变量：

![img](/home/hedge/Typora/Temp-image/v2-4b5e17a6631dc0401ddace71a82f83e3_r.jpg)

这时才真正切换到 root 用户了。

而且你可能发现了，加短线与不加短线，是有区别的：

![img](/home/hedge/Typora/Temp-image/v2-8507b57c732d8a99023d5c60246e675b_720w.jpg)

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

![img](/home/hedge/Typora/Temp-image/v2-09307e1a492e37f60fc51064064ab797_720w.jpg)

事实上，把用户加入组其实就是修改了这个文件，所以我们也可以通过修改这个文件的方式把某个用户加入某个组，比如如果我把文件第一行的内容改成这样：

![img](/home/hedge/Typora/Temp-image/v2-cb19c13c7e02ee12838325855a7a8171_720w.jpg)

就表明我把 user2 用户（如果user2用户存在的话）也加入了 root组。同理，从组中删除用户也可以通过修改 `/etc/group` 文件的方式实现。



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



# Chapter3 实践经历

## 1. 查看系统配置

### CPU

```bash
$ lscpu
```

### GPU

> 



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



