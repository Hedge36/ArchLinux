# NoteBook Sever For Windows

## 1. 前提

> **使用的服务器全局/用户环境配置了Anaconda，并在任意环境中安装了Jupyter notebook。**检查方法如下：
>
> ```Shell
> ### SHELL ###
> $ conda --version
> conda 4.11.0	
> ```
>
> 出现如上版本信息则表明服务器全局/用户环境下配置有Anaconda（通常Linux系统下环境路径会自动添加），若无则需先行安装。
>
> <u>备注：SHELL是SSH远程连接终端模拟器，如Cywin，即需先行通过SSH登录检查。此外，以下全部命令均在该终端模拟器上执行。</u>。
>
> *进一步介绍参考附录1*。



## 2. 基本操作说明

### 2.1 SSH连接

> 不同于直接的SSH连接，要正常使用服务器的Jupyter notebok sever，需要增加连接参数，基本命令格式如下，其中`<name>`表示用户输入参数。
>
> ```SHELL
> ### SHELL ####
> $ ssh -L <Port1>:<Host>:<Port2> <User>@<Sever_Address>
> # 对于lttws用户，命令如下
> $ ssh -L 8000:localhost:8888 lttws@211.66.130.58
> ```
>
> 命令具体用法可不作了解，*有关该命令的进一步解释参考附录2*。

### 2.2 Notebook Sever

> 输入密码**登录服务器**后，需要先在服务器上**打开notebook Sever**，参数`--no—browser`表示不打开浏览器（理论上应该是必须项，未深入研究）：
>
> ```SHELL
> $ jupyter notebook --no-browser
> ```
>
> 此时终端模拟器会出现一堆提示语，其中包括：
>
> ```SHELL
> http://localhost:8888/..../ token=.....
> ```
>
> 前边的好像是这些，随后将token=后边的值复制下来，**打开浏览器访问**如下网页即可：http://localhost:8000/，首次登录需要输入token值，即在提示语中复制的token值，亦可于下面设置密码。输入后即进入Jupyter页面，此时基本的操作即完成。
>
> *有关jupyter进一步配置设置参考附录3。*



## 3. 附录

### 附录1 基本介绍

> 该端口映射类似于<u>服务器将jupyter部署到一个网页上，我们通过`ssh -L`进行局域网连接访问该网页</u>，因此，其实本地可以没有jupyter或者anaconda，只需服务器有即可。
>
> 非ROOT用户安装Anaconda参见[这里](https://blog.csdn.net/qq_34769162/article/details/107687659)，其中最后的环境路径操作无需进行，安装最后一步时Anaconda会询问用户是否进行conda初始化，其中包括路径的自动添加。

### 附录2 SSH PORT设置

> Port是计算机进程间通信的端口，此处理论上可以随意设置，但是实际上最好不要这么做，随意输入的端口可能会挤占系统服务端口，导致系统服务出现异常，因此。通常采用端口包括`8000`以及`8888-8899`即可。其中`8000`是本地端口，`8888`是服务器端口，`8888`是Jupyter notebook Sever采用的默认端口，可以通过启动命令添加参数`--port`指定，亦可在配置文件中修改，此处不做展开。
>
> 需要注意的是，**端口是独占的**，意味着当有一个用户启动Sever使用`8888`端口之后，其他人无法再使用，此时第二个用户再启动Notebook Sever时将重新分配端口，默认为`8889`（在启动服务时会有英文提示语说明当前端口被挤占，以及新的端口值），这时需要退出登录（或许有重新改变端口映射的其他方法，未深入研究）修改原命令中`ssh -L 8000:localhost:8888`为`ssh -L 8000:localhost:8889`，此处的第二个Port为自定义端口。

### 附录3 Jupyter配置

> 使用需要注意以下事项：
>
> 1. **以上命令均在base环境中执行**，若需要使用虚拟环境，请在启动notebook Sever之前激活虚拟环境，特别的以lttws为例：
>
> 	```SHELL
> 	# For long 
> 	$ conda activate basetorch
> 	# For alias
> 	$ ca basetorch	# 激活torch环境
> 	$ cda			# 关闭torch环境
> 	```
>
> 2. 较新版的notebook sever可能出现以下警告，暂时不理；
>
> 	```SHELL
> 	'password' has moved from NotebookApp to ServerApp. This config will be passed to ServerApp. Be sure to update your config before our next release
> 	```
>
> 3. 更进一步的notebook配置，如Kernel内核、Env虚拟环境管理及其他配置，此处不再展开，参考`Anaconda_for_Linux.pdf`。



# For Linux

> 基本操作一样，只是更简单一些。
