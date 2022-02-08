# Chapter1 云服务器操作

## 1. 远程服务器操作实例

### 1.1 校内网VPN-openconnect

> 经测试，在ArchLinux（本机）中，登录sysu最方便的方式是采用openconnect连接。
>
> 最直接的连接方式，使用root超级权限启动openconnect连接服务器，并在随后的提示符输入用户名和密码。对于更复杂的连接方式，可以采用下面的方法连接，输入user用户名和服务器地址，随后在提示后输入密码。
>
> 其中，校内网服务器地址为https://ocvpn.sysu.edu.cnz，用户名及密码为NetID的帐号和密码。

```bash
$ sudo openconnect vpnserver
$ sudo openconnect -u user --passwd-on-stdin vpnserver
```

> 很多VPN提供者都会根据权限分组，不同用户组拥有不同的访问设置，如全频道连接和半频道连接，因此，想要显示不同权限组及权限差异信息，一般通过以下命令实现（该命令不需要超级权限）：

```bash
$ openconnect --authenticate vpnserver
```

### 1.2 SSH操作

| Operation                                                   | Description    |
| ----------------------------------------------------------- | -------------- |
| ssh **user**@**server.address**                             | 登陆远程服务器 |
| cd /www/wwwroot/**server.address/**                         | 跳转路径       |
| scp -r localpath **user**@**server.address**:**sever.path** | 上传文件       |



# Chapter2 搭建Linux服务器

## 1. Linux搭建SSH服务  

> 为了实现SSH功能你得确定你的Linux上有安装了SSH服务，Ubuntu可能没有安装，但Arch一般已经内置有。如果采用的Linux系统没有安装ssh服务，只需要安装一个开源的SSH工具叫做OpenSSH，就可以把你的Linux变成一个服务器。安装方法通常直接采用对应的包管理即可，以下所有命令都以Ubuntu和ArchLinux为例。
>

```shell
$ sudo apt-get openssh-server	# Ubuntu
$ sudo pacman -S openssh		# Arch
```



## 2. Linux SSH

> Linux搭建SSH服务后，即可直接通过SSH登录，登录后在提示下输入密码即可，其登录命令如下：
>

```shell
$ ssh user@sever.address
```

> 至于如何查看IP地址，对于Ubuntu,可以通过`ifconfig`工具查看（如果没有，则需要自行安装），对于ArchLinux，可以通过`ip address`查看，这里展开说明Arch。
>

```bash
$ ifconfig					# Ubuntu
$ ip address | grep inet	# Arch
	inet 127.0.0.1/8 scope host lo
    inet6 ...... 
    inet 192.168.0.0/24 ......
    inet6 ......
    inet6 ......
```

> 如上述所示，第一个inet即为本机地址，第二个inet即为本机在服务器上的IP地址。



##  3. Windows SSH

在Windows上，SSH不像Linux和MacOS那样常用, 而且Windows的系统内核也和Linux不太一样. 所以我们用一个软件来实现SSH比较合适。PuTTY是一个开源、免费，而且常被使用的SSH软件。首先，我们得下载这个软件。

[PuTTY 下载页面](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

在这个下载界面中, 你会看到类似这样的界面, 确认你 Windows 电脑是多少位的 (32-bit 或 64-bit), 然后选择一个适合你电脑的 `.msi` 安装包.

[![04-02-01.png](/home/hedge/Typora/Temp-image/04-02-01.png)](https://static.mofanpy.com/results/linux-basic/04-02-01.png)

安装好之后, 在开始菜单中找到 PuTTY, 并打开 PuTTY, 你会看到下面这样. 然后在 Host name (or IP address) 那填上被控制的 Linux 的 IP. 获取被控制 Linux IP 的方法就是在这台 Linux 的 terminal 上输入:

确保 `ifconfig` 能用后, 输入 `ifconfig`, 然后找和 `inet addr` 有关的那一串 IP 地址. 之后将这个 IP 地址输入到你的 PuTTY 的 Host name (or IP address) 位置. 默认情况下, 是不用修改 port 的数值的.

[![04-02-02.png](/home/hedge/Typora/Temp-image/04-02-02.png)](https://static.mofanpy.com/results/linux-basic/04-02-02.png)

点击 Open 按钮, 你就能登录 Linux 啦, 它还会跳出一个小窗, 让你确认这台电脑是不是你要链接的电脑. 如果你在自己家的局域网内,就不用担心安全问题, 直接点 Yes 就好.

[![04-02-03.png](/home/hedge/Typora/Temp-image/04-02-03.png)](https://static.mofanpy.com/results/linux-basic/04-02-03.png)

最后你需要输入 Linux 的用户密码作为确认. 然后就能顺利开始在 Windows 上操控 Linux 啦. 这里我用 Windows 操控了一下我的 Raspberry Pi, 树莓派. 一个微型电脑的 Terminal.

[![04-02-04.png](/home/hedge/Typora/Temp-image/04-02-04.png)](https://static.mofanpy.com/results/linux-basic/04-02-04.png)



## 4. Andriod SSH

安卓里有很多 ssh 的 app. 苹果肯定也不少. 其实你只要用 SSH 搜搜 app store 里面. 里面就会有非常多的可用 app. 我以 JuiceSSH 举例. 其他的应该都大同小异.

[![04-03-01.png](/home/hedge/Typora/Temp-image/04-03-01.png)](https://static.mofanpy.com/results/linux-basic/04-03-01.png)

下载好 JuiceSSH. 打开你的这个 app, 如果你还没有创建过任何 ssh 链接. 你将需要点击 Connections, 自己创建一个连接.

[![04-03-02.png](/home/hedge/Typora/Temp-image/04-03-02.png)](https://static.mofanpy.com/results/linux-basic/04-03-02.png)

下一步中, 我们唯一需要的就是你要连接去, ssh 去的 IP 地址. 在你的 Linux terminal 中输入 `ifconfig` 获得你现在的 IP 地址, 一个以 `inet` 开头的地址, 通常是 192.168.0.xxx 如果你的 `ifconfig` 指令不管用, 说明你还没有安装一个东西, 所以在 terminal 下输入

```shell
$ sudo apt install net-tools
```

就能使用 ifconfig 了. 然后将找到的 ip 地址原封不动的放在 Address 这一栏中. 接着点击右上角的那个勾确定添加这个连接.

[![04-03-03.png](/home/hedge/Typora/Temp-image/04-03-03.png)](https://static.mofanpy.com/results/linux-basic/04-03-03.png)

确定后它会跳出一个窗口, 让你确认你要连接上的电脑是否是你真正要连接上的电脑. 如果你在自己家中的路由器下, 就不用担心, 别人也很难黑得了你. 如果你在一个公用路由下. 你还是得再三检查一下, 免得到时候被黑客攻击.

[![04-03-04.png](/home/hedge/Typora/Temp-image/04-03-04.png)](https://static.mofanpy.com/results/linux-basic/04-03-04.png)

然后就是输入你 Linux 电脑的用户密码了. 确认后你就能在手机上正常使用 ssh 控制你的 Linux 电脑.

[![04-03-05.png](/home/hedge/Typora/Temp-image/04-03-05.png)](https://static.mofanpy.com/results/linux-basic/04-03-05.png)

[![04-03-06.png](/home/hedge/Typora/Temp-image/04-03-06.png)](https://static.mofanpy.com/results/linux-basic/04-03-06.png)

加上前面用 MacOS, Windows 和这节用手机 ssh 去 Linux 的教程, 我相信, 你正开心地倒腾着. 不过有时候你不太适应用 terminal 来操控电脑. 想要用一个可视化的界面更直观的操控 Linux 电脑. 后面要提到的 VNC 和 Teamviewer 就是你要了解的啦~



## 5. SSH key

不过你还可以更进一步现在你每 SSH 登录一次 Linux， 都需要输入密码如果你登录次数很频繁而却你的密码又设置得很长这就非常麻烦。 还好我们可以通过提前设置一个保密协议来让你的 Linux 识别出哪些电脑能不用密码登录。 这就是 `public/private rsa key`。

我们将在 Mac 或者 Linux (控制电脑) 上生成一个 `public/private keypair` (公钥和私钥)然后将公钥(public key) 复制到要被远程的 Linux 上。 这样当你有私钥的控制电脑要远程操控这台有公钥的 Linux，他会帮你识别配对的。就不用每次都要输入被远程的电脑密码了。

所以首先我们还是用我的 Mac demo，在 mac的Terminal上输入指令`ssh-keygen`创建公钥和私钥它会提示你要保存这些锁的地方。我们就用它默认的地方比较好。 所以回车确定.

```shell
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/MorvanZhou/.ssh/id_rsa):
```

确定后它会弹出下面这个要你来确定你是否想要一个保障密码如果你确定你的局域网是安全的这个都可以不填。 我就不填所以我直接回车。

```shell
Enter passphrase (empty for no passphrase):
```

然后它会要求你再次确认回车

```shell
Enter same passphrase again:
```

最后它会显示类似于这样的东西告诉你你的锁都已经生成好了。

```shell
Your identification has been saved in /Users/MorvanZhou/.ssh/id_rsa.
Your public key has been saved in /Users/MorvanZhou/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:yVr3PAPmxVO1lBd7KvqBsBCZSE8mdYce8mjBiUfRDVE MorvanZhou@Morvan
The key's randomart image is:
+---[RSA 2048]----+
|    o=*++*E    o+|
|   ..**++..   .o+|
|    ..=* .    .oo|
|      ooo. . . ..|
|     .. S + = .  |
|       + * B o   |
|      . . + *    |
|           . +   |
|            .    |
+----[SHA256]-----+
```

接着我们就要将这个生成好的 公钥 给复制去你的 被控制的 Linux。 指令结构还是和上面一样。

```shell
$ ssh-copy-id [被控制的用户名]@[它的ip]
```

我被控制的 Linux 用户叫 morvan， 他的 IP， 我通过了上面描述的方式找到了。 所以我就输入下面这样。 回车后他会要求你输入一次 被控制端电脑的密码。

```shell
$ ssh-copy-id morvan@192.168.0.114

/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/Users/MorvanZhou/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
morvan@192.168.0.114's password:
```

密码正确后它将输出并告诉你的怎么用 ssh 登录被控制端的电脑。

```shell
Number of key(s) added:        1

Now try logging into the machine, with:   "ssh 'morvan@192.168.0.114'"
and check to make sure that only the key(s) you wanted were added.
```

最后我们开开心心地在 Mac/Linux ssh 被控制的电脑吧~ 这次登录的时候没有被要求输入任何密码~

```shell
ssh morvan@192.168.0.114

Welcome to Ubuntu 16.04.3 LTS (GNU/Linux 4.4.0-96-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

147 packages can be updated.
53 updates are security updates.

Last login: Mon Oct 16 08:36:26 2017 from 192.168.0.111
```



## 6. 远程桌面控制软件

### Teamviewer  

Teamviewer 其实已经发展得很成熟了. 它是一个跨平台的远程操控软件. Windows, MacOS, Linux, 手机都可以下载使用. 它会通过外网, 将你的被控制电脑桌面投影到你的控制电脑上. 不过的流畅度, 速度大大取决于你的网速. 如果你是想做一个小规模, 控制局域网内(电脑都在同一个路由下)的电脑. 我觉得还是 VNC 快一点, 因为它不走外网. 当然, 最快的还是 SSH 啦, 都不用输出图像, 直接代码控制而已. 如果你对 SSH 的方式感兴趣, 这里有我制作的几节入门教程:

- [从 Mac 或 Linux 远程 ssh 控制 Linux](https://mofanpy.com/tutorials/others/linux-basic/ssh-from-linux-or-mac)
- [从 Windows 远程 ssh 控制 Linux](https://mofanpy.com/tutorials/others/linux-basic/ssh-from-windows)
- [从手机远程 ssh Linux](https://mofanpy.com/tutorials/others/linux-basic/ssh-from-phone)

如果要用图像化的方式控制电脑, 首先我们从最方便的说起. [TeamViewer 的官网](https://www.teamviewer.com)提供了很多下载安装方式.

[![04-04-02.png](/home/hedge/Typora/Temp-image/04-04-02.png)](https://static.mofanpy.com/results/linux-basic/04-04-02.png)

你可以根据你的系统选择, 而且如果是家用, 它就是免费的, 只有企业用才是收费.

他的程序界面是这样的, 功能其实很完善, 左面是一些你自己的信息, 你可以提供这些信息给你的朋友, 要他们控制这台电脑. 中间的区域是你可以利用朋友发来的信息来控制朋友的电脑. 右边的区域是你自己的管理区域, 你可以用一个账号管理你想连接的电脑. 这样非常方便.

[![04-04-03.png](/home/hedge/Typora/Temp-image/04-04-03.png)](https://static.mofanpy.com/results/linux-basic/04-04-03.png)

不过就像之前说的. 这种远程控制是基于互联网的, 万一你网速不好, 而且你只想在局域网里用, 卡到想死的心都有. 所以这种情况你就可以考虑 VNC.

​    

### VNC  

其实 VNC 是一种软件的统称. 只要你的 Linux 架设好了一个服务器 (Server) 的 VNC, 客户端, 比如你的 Mac, 手机, 只要安装任何一种 VNC 客户端软件就能链接上服务器端的电脑啦. 如果你手头有一个 Raspberry Pi (树莓派), 会用 VNC 对你很实用. 那么首先, 我们就来设置这个服务器端的 VNC 吧. 打开你的 Linux 电脑, 打开 Terminal. 输入:

```shell
$ sudo apt-get install x11vnc
```

确认你的 Linux 用户密码, 就能安装这个最常用的 x11vnc 软件啦. 这个软件的使用, 设置非常简单. 安装好后, 最好给你的 x11vnc 设置一个密码. 我不设密码时, 用 Mac 还登不上, 一定要设完密码,用密码登录 Linux 的 VNC server 才能上.

所以设置密码的过程就是在你的 Linux Terminal 输入下面这样, 然后它会提示你要输入你要的密码, 这个密码是用来连接 VNC 的时候, 登录用的.

```shell
$ x11vnc -storepasswd

Enter VNC password:
Verify password:
Write password to /home/morvan/.vnc/passwd?  [y]/n y
Password written to: /home/morvan/.vnc/passwd
```

设置好之后, 在你的 Linux terminal 中输入下面指令, 要求用密码形式来开启 VNC 的 server.

```shell
$ x11vnc -usepw
```

**如果你使用的是 ubuntu 17.10, 截止至目前 (2017年10月27日) 对于 VNC 还有一个 bug 没有修复. 所以 17.10 版本的 Ubuntu 如果你尝试上面的方式发生下面这种问题, 你就要尝试一下我接下来说的方法了.**

```shell
X Error of failed request: BadMatch (invalid parameter attributes)
Major opcode of failed request: 73 (X_GetImage)
Serial number of failed request: 41
Current serial number in output stream: 41
```

首先这个问题, 我查了很久, 最后发现是新版 ubuntu 的桌面显示升级了, 好像是变成3D, 然后以前的 2D 形式的 x11vnc 都不支持. 所以我们要换一种形式的桌面. 首先要做的就是 logout 你的电脑. 在桌面右上角, 选着你的用户, 然后 logout.

[![04-04-031.png](/home/hedge/Typora/Temp-image/04-04-031.png)](https://static.mofanpy.com/results/linux-basic/04-04-031.png)

然后再选择不同的桌面方式 (Xorg) 登录 ubuntu. 这样一来, 如果再重复上面的 x11vnc 启动方式, 你就不会报错了.

[![04-04-032.jpeg](/home/hedge/Typora/Temp-image/04-04-032.jpeg)](https://static.mofanpy.com/results/linux-basic/04-04-032.jpeg)

最后, 如果出现频繁跳出 x11vnc 的现象, 尝试在开启 x11vnc 的时候直接输入这个参数, 让它永远运行.

```shell
$ x11vnc -usepw -forever
```

#### 用 Mac 连接 VNC  

开启完之后, 使用 Mac 来连接 Linux 的 VNC 很方便, 在 Mac 中, 有一个软件叫 Screen Sharing. 打开它, 如果你 Linux 在局域网的 IP 地址(可以在 Linux 中输入 `ifconfig` 查到). 点 Connect, 最后输入你刚刚设置的 VNC 密码, 就能连上啦

[![04-04-04.png](/home/hedge/Typora/Temp-image/04-04-04.png)](https://static.mofanpy.com/results/linux-basic/04-04-04.png)

[![04-04-05.png](/home/hedge/Typora/Temp-image/04-04-05.png)](https://static.mofanpy.com/results/linux-basic/04-04-05.png)

[![04-04-06.png](/home/hedge/Typora/Temp-image/04-04-06.png)](https://static.mofanpy.com/results/linux-basic/04-04-06.png)

​    

#### 用 Windows 连接 VNC  

至于 Windows 呢, 其实有很多选项, 我们已经在 Linux 端设置好了一个 VNC server. 在 Windows 端, 我们需要的只是一个 VNC client. 而有很多软件可以实现 VNC client 这个功能. 我在下面列举一些:

- [TightVNC](http://www.tightvnc.com/) (免费)
- [RealVNC](https://www.realvnc.com/) (免费)

RealVNC 有两种选项, 一个是 [VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/), 用来做 client 端的(控制). 一个是 [VNC connect](https://www.realvnc.com/en/connect/download/vnc/), 用来做 server 端的(被控制).

Client 端的 VNC 操作流程都很简单. 只要求要一个 server 端的 IP 和他的密码就好.

#### 用 Linux 连接 VNC  

Linux 的话, 它自带就有一个 VNC 软件. 只要你在右上角搜一下 VNC, 那个被我圈出来的软件就是一个 Client 端的 VNC. 点开它, 输入 server 端的 IP 和他的密码就好.

[![04-04-07.png](/home/hedge/Typora/Temp-image/04-04-07.png)](https://static.mofanpy.com/results/linux-basic/04-04-07.png)



# Chapter3 云服务器的使用                                                                                    

## 1. 云端运行  

> 在Linux搭建了服务器环境后, 假如我在操控端写代码，在我的 `Desktop` 文件夹下写好了一个 Python 脚本 `machine_learning.py`。但是我想拿 Mac 来做点其他事，不想让这个脚本在我的 Mac 上发光发热，那么我们就 ssh 远程推送到旁边空闲的 Linux 去运算吧。
>

比如这个 Python 脚本是这样的.

```python
import platform2

a = 3
for i in range(9999):
    a += i5
print("Finish job, result=%i" % a)
print("This is", platform.system())
```

随后登录服务器，具体登录过程省略。

```shell
$ ssh morvan@192.168.0.114 python3 < ~/Desktop/machine_learning.py

Finish job, result=49985001
This is Linux
```

> 注意这和我们之前用 SSH 类似, 不过这次我们加了一个 python 文件给服务器端. 这个文件的转换方式就用 `<` 来代替. 而且因为这是一个 Python3 文件, 所以我在 ip 后面写的是用 `python3` 在云端执行本地的这个文件.
>



## 2. 文件传输  

如果是有很多的 Python 文件怎么办呢? 有时候 Python 文件是一环扣一环，这个文件里调用了那个文件的东西。这时我们就能先全部复制所有必须文件去 Linux 的缓存区或者桌面，然后再使用 ssh 在 Linux 云端的运行传送过去的文件。

比如我现在需要两个 Python 文件才能运行, `b.py` 如下:

```python
# This is b.py


def inner_func():
    print("This is a function in b")
```


还有一个 `a.py` 需要调用 `b.py` 才能运行.

```python
# This is a.py
from b import inner_func

inner_func()
```

接着我们要做的就是将这两个文件先复制去 Linux 云端, 然后在云端运行 `a.py`。下面所有的操作都是在本地执行的, 我们没有跑去云端打代码. 输入 `scp` (secure copy), 加密传输复制 `~/Desktop/{a,b}.py` 在我桌面上的 `a.py` 和 `b.py` 两个文件到云端`morvan@192.168.0.114`的桌面 `~/Desktop`

```shell
$ scp ~/Desktop/{a,b}.py morvan@192.168.0.114:~/Desktop

a.py                                          100%   37     6.3KB/s   00:00
b.py                                          100%   54     8.9KB/s   00:00
```

执行的话, 和上面的步骤有点不一样, 在本地用 ssh 去云端, 但是 ssh 的时候同时发送一条指令去执行 `a.py`. 这条指令我们用 `""` 给框起来, 说明是要发送去云端再执行的指令.

```shell
$ ssh morvan@192.168.0.114 "python3 ~/Desktop/a.py"

This is a function in b
```

同样, 如果你在云端的程序会产生一些结果文件, 我假设 `b.py` 是在云端运行完 `a.py` 而产生的新文件, 而我在本地电脑需要这个产生的文件. 我可以直接用 `scp` 的方式将这个 `b.py` 复制回来. 所以你会发现, `scp` 前一个参数是从哪开始复制, 后一个参数是复制去哪. 这样完了以后, 在我的 Mac 桌面上就产生了一个 `result` 文件.

```shell
$ scp morvan@192.168.0.114:~/Desktop/b.py ~/Desktop/result
```

这样一来一回，我们总结一下走过的流程。

> - 本地有要运行的文件
> - 单个文件的话可以直接 ssh 去云端运行
> - 多个文件可以先复制去云端, 然后在 ssh 运行
> - 如果在云端有产生文件, 可以用 scp 复制回来



## 3. gym 的强化学习注意事项  

如果你云计算的是强化学习, 而且有时候会要使用 gym 模块来模拟, 有一个事情需要注意. 如果不注意, 你有可能运行 python 会出错.

这个问题是, 如果你 ssh 在云端执行一个会打开窗口程序的指令, 比如用 ssh 在云端打开浏览器等, 默认是不允许的. 你必须设置一下这个参数. 比如我要打开 Firefox 浏览器窗口. 那么在 `firefox` 指令前, 需要加上 `export DISPLAY=:0`, 并用 `;` 隔开, 标明执行的先后顺序.

```shell
$ ssh morvan@192.168.0.114 "export DISPLAY=:0; firefox"
```

所以这个问题在强化学习中也存在, 如果你在强化学习的代码中有打开视窗的操作, 比如下面这句话会将 gym 模块的环境显示在屏幕上.

```
# 在你的强化学习Python脚本中2
env.render()
```

那么你就要用上面描述的方法执行这个脚本. 如果碰到类似的需要打开视窗的时候, 都需要这样做.

```shell
$ ssh morvan@192.168.0.114 "export DISPLAY=:0; python3 reinforcement_learning.py"
```





## 4. 云端共享与云计算

云端计算固然方便, 如果让你的电脑上直接显示云端的文件, 是不是更方便呢? 哈哈, 这次我就来探讨一下可行的方式.

假设你的情况是这样: 有两台电脑(其中一台是 Linux) ，电脑们都在同一个局域网 ，想把那台 Linux 当做云端，做云计算，又不想来回复制文件，能不能把云端的某个文件夹分享到我的本地，在本地及时修改这个共享文件夹的文件，不是云计算也行，只是想在几台电脑中共享文件。

[![05-02-01.png](/home/hedge/Typora/Temp-image/05-02-01.png)](https://static.mofanpy.com/results/linux-basic/05-02-01.png)

为解决上述问题，我们可以单独创建一个要分享的文件夹, 这样你就知道自己要将哪个文件夹里的文件分享给大家了. 比如说, 在 Linux 的 Home 目录下创建一个 Shared 文件夹. 你可以用鼠标来创建或者直接在 terminal 中输入指令。

```shell
$ mkdir ~/Shared/
```

[![05-02-02.png](/home/hedge/Typora/Temp-image/05-02-02.png)](https://static.mofanpy.com/results/linux-basic/05-02-02.png)

有了这个 Shared 文件夹以后, 我们来对这个文件夹动手脚. 右键选择 `Local Network Share`, 之后你会跳出来一个 Folder Sharing 的窗口, 在这个窗口中, 勾选 Share this folder.

[![05-02-03.png](/home/hedge/Typora/Temp-image/05-02-03.png)](https://static.mofanpy.com/results/linux-basic/05-02-03.png)

如果你第一次做这件事, 当你选定的时候, 应该会出现上面那个要求安装东西的窗口, 点击 `install` 就好, 他会帮你安装必要组建. 安装好之后, 还会弹出一个重启 session 的窗口, 重启它. 然后给你的这个文件夹起一个 响亮 的名字, 这个名字会出现在其它的电脑上. 所以, 我就起了一个名字叫 Shared. 哈哈.

[![05-02-04.png](/home/hedge/Typora/Temp-image/05-02-04.png)](https://static.mofanpy.com/results/linux-basic/05-02-04.png)

最后如果你会在其它电脑上编辑这个 Shared 里的文件, 那你就需要勾选 Allow others to create and delete files in this folder. 我觉得最下面那个选项不要选比较好, 如果选了, 任何在这个局域网内的人都能玩弄你的文件. 你肯定不想这样.

这还不够, 在 terminal 中, 我们最好给这个分享文件设置一个密码. 如果有人想要登录这个分享文件, 就需要密码登录. 设置密码的步骤很容易, 你只要在**云端的 terminal** 中输入下面内容, 将分享文件夹的账号密码设置成你 linux 用户的账号密码就好了, 好记又方便.

```shell
$ sudo smbpasswd -a 用户名      # 比如下面我的用户名是 morvan
$ sudo smbpasswd -a morvan
```

之后它会要求你输入用户名的密码, 然后再设置分享的密码 `New SMB password`, 再 `Retype new SMB password`. 完了以后就大功告成, 你就能在其它电脑上找到这个文件夹, 使用这个用户名和密码查看文件啦.

​    

### Windows 找到云端的分享文件  

Windows 找到共享的文件也非常简单, 只需要找到你的局域网电脑们就好了. 当你打开文件浏览器. 找到 网络, 或者是网上邻居 然后找到你的 Linux 电脑, 输入之前设置的账号密码. 就能查看你共享的 Linux 文件夹啦.

[![05-02-08.jpg](/home/hedge/Typora/Temp-image/05-02-08.jpg)](https://static.mofanpy.com/results/linux-basic/05-02-08.jpg)



### Mac 找到云端的分享文件夹  

我们已经设置好的云端的共享文件. 接着就是在其他电脑上找到这个共享文件. 我用 MacOS 来演示一遍. 首先你需要找到这个共享的地方. 打开你的 `Finder` 文件管理器, 然后在上面的菜单中找到 `Go`, 点击 `Network`,

[![05-02-05.png](/home/hedge/Typora/Temp-image/05-02-05.png)](https://static.mofanpy.com/results/linux-basic/05-02-05.png)

然后找到你的计算机名, 我这里是 `MORVAN-LINUX`, 之后点击 `connect as`, 这个意思是说要登录上之前设置好的账号密码. 如果没有经过这一步, 是无法打开 Shared 文件夹的.

[![05-02-06.png](/home/hedge/Typora/Temp-image/05-02-06.png)](https://static.mofanpy.com/results/linux-basic/05-02-06.png)

点击 `connect as` 之后, 我们就按要求填写刚刚的你在 Linux 上设置的账号密码就好.

[![05-02-07.png](/home/hedge/Typora/Temp-image/05-02-07.png)](https://static.mofanpy.com/results/linux-basic/05-02-07.png)

最后成功登录上, 你就能用这个云端文件夹的内容啦.

[![05-02-01.png](/home/hedge/Typora/Temp-image/05-02-01.png)](https://static.mofanpy.com/results/linux-basic/05-02-01.png)

现在我就能直接在我的 Mac 上编辑云端的文件, 比如做一个 Python 的项目, 然后 [SSH](https://mofanpy.com/tutorials/others/linux-basic/ssh-from-linux-or-mac) 去 Linux 云端运行这个写好的文件. 方便又不占你 Mac 的空间.
