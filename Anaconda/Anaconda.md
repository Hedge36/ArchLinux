# Anaconda 使用教程(Linux)

> **以下命令基于Linux Terminal而非anaconda prompt窗口。**
>
> 进入环境后，在终端最后部的(env)中显示有环境名称，默认为`base`。

## 1. 频道设置

> 设置anaconda包下载的来源，有代理没啥事还是别设置了吧。

```bash
$ conda config --add channels <url>						# 添加镜像源
$ conda config --set show_channel_urls yes		# 设置搜索时显示通道地址
$ conda config --show channels								# 显示添加的镜像源
$ conda config --remove channels <url>				# 删除已添加的镜像源
$ conda config --remove-key channels				# 还原镜像源设置
```

| Ref-Url                                                      | Description  |
| ------------------------------------------------------------ | ------------ |
| https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/ <br />https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/<br />https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/ | 清华镜像源   |
| https://mirrors.aliyun.com/pypi/simple/                      | 阿里云镜像源 |
| https://pypi.mirrors.ustc.edu.cn/simple/                     | 中科大镜像源 |
| https://pypi.douban.com/simple/                              | 豆瓣镜像源   |



## 2. 环境操作

> 也可以通过`anaconda-navigator`进行调整。cli下命令如下：

```bash
# 查看现有虚拟环境
$ conda env list 		# 或以下方式
$ conda info -e

# 创建新的虚拟环境
$ conda create -n <env_name> python=3.8 	# 默认为当前版本

# 激活与关闭虚拟环境
$ conda activate <env_name>
$ conda deactivate        			# 不用接环境名

# 删除虚拟环境或某个包
$ conda remove -n <env_name> --all				# 删除虚拟环境
$ conda remove --name <env_name>  <package_name>		# 删除环境中的某个package

# 重命名
$ conda create -n <new_env_name> --clone <env_name>		# 复制一份
$ conda remove -n <env_name> --all				# 删除原本的环境
```



## 3. 更新操作

```bash
$ conda update conda				# 更新conda（往往这个就够了）
$ conda update --all					# 更新anaconda所有库
$ conda update anaconda			# 更新anaconda
$ conda install spyder=1.0.0	# 更新spyder
$ conda install python 				# 更新python
```



## 4. 其他操作

> `conda`全部命令，可通过`conda help`查询。
>
> 基本信息通过 `conda info` 来查看。

### 4.1 包管理

> 基本的包管理，包括安装、卸载、查询等，其中，包的安装也可以通过 pip 来实现。

```shell
$ conda search <package>	# 根据package搜索有关的包
$ conda install <package>	# 安装指定包
$ conda uninstall <package>	# 卸载当前环境下指定包
$ conda install anaconda	# 安装anaconda平台集成的所有包
$ conda list				# 显示已安装的所有包
```

### 4.2 版本管理

> 有时会出现版本冲突导致的异常等或其他情况，以下命令可以使环境倒退版本。
>
> **请注意，慎重使用，尤其是版本回退的同时可能导致 conda 版本降低的情况！！！**

```shell
$ conda list -n <env_name> --revisions		# 查看环境历史版本，默认为 base
$ conda install --rev <number>		# 回退到第 N 个版本
```



## 5. Jupyter

### 1. Command

#### Synopsis

```bash
$ jupyter <subcommand> [options]	# Command
```

#### Description

> **Commands like `jupyter notebook` start Jupyter applications.** 
>
> The `jupyter` command is primarily a namespace for subcommands. A command like `jupyter-foo` found on your `PATH` will be available as a subcommand `jupyter foo`.
>
> The **jupyter** command can also be used to do actions other than starting a Jupyter application.

#### Command options

> - **-h**, **--help**
>
> 	Show help information, including available subcommands.
>
> - **--config-dir**
>
> 	Show the location of the config directory.
>
> - **--data-dir**
>
> 	Show the location of the data directory.
>
> - **--runtime-dir**
>
> 	Show the location of the runtime directory.
>
> - **--paths**
>
> 	Show all Jupyter directories and search paths.
>
> - **--json**
>
> 	Print directories and search paths in machine-readable JSON format.



## 6. Notebook Sever

### 6.1 Kernel

#### Basic Operaion

> 有关内核的一些基本操作见下：
>
> ```shell
> $ jupyter kernelspec remove <kernelname>	# 删除内核
> $ jupyter kernelspec list					# 查看当前环境下所有内核
> ```

#### C++

> 安装完毕后，需要进入C++环境再打开notebook，否则无对应内核。若无法正常连接到内核，则重新安装内核即可。以下教程为创建虚拟环境下的C++，也可以直接创建在默认环境下。

```shell
$ conda create -n <env_name>				# 创建环境
$ conda activate <env_name>					# 激活环境
$ conda install jupyter notebook			# 安装jupyter
$ conda install xeus-cling -c conda-forge	# 安装C++内核
$ jupyter kernelspec list					# 打印现有内核
```

#### C

```Shell
$ conda create -n clang
$ conda activate clang
$ conda install jupyter notebook		# 至此均为新环境执行步骤
$ pip install jupyter-c-kernel
$ install_c_kernel --user				# 安装在当前环境下
$ jupyter kernelspec list
$ jupyter notebook
```

#### R

> R语言内核的安装比较特殊，需要直接进入R console，而不是普通终端。该命令会直接在默认jupyter notebook环境下创建内核（新建环境需要使用conda安装jupyter和notebook）。

```R
> install.packages("IRkernel")			# 安装内核
> IRkernel::installspec(user = FALSE)	# 全局安装(需要sudo R)
> IRkernel::installspec()				# 用户安装
```

#### python

> 一般情况下，默认内核为python3（base），其他虚拟环境需要另外加载，依照以下操作即可，其中`envname`为需要加载的虚拟环境名称。

```bash
$ conda activate envname
$ conda install ipykernel				# 如果已经在vscode上运行过，则已安装
$ python -m ipykernel install --name envname			# 不支持-n短命令
$ python -m ipykernel install --user --name envname 	# 安装局部内核
```

---

### 6.2 Start

#### Local

> 本地jupyter服务较简单，可以直接通过以下命令启动Jupyter本地服务。

```bash
$ jupyter notebook 					# Open notebook
$ jupyter notebook --port 8000		# Specify port id(8000 for default)
$ jupyter notebook --no-browser		# Don't open brower in local;
```

#### Sever

> 使用本地端口远程登陆，在本地启动端口，把本地端口数据转发到远端。意即为在本地起端口(8000)，映射到服务器用户的localhost:8888中，其中localhost:8888是目标服务器默认的jupyter notebook端口。

```shell
$ ssh -L 8000:localhost:8888 <user>@<sever.address>
# ssh -L IP1:PORT1:HOST2:PORT2 USER@HOST2
```

> 登陆后于服务器打开notebook sever

```shell
$ jupyter notebook --no-browser
```

> 打开本地浏览器访问端口`localhost:8000`（默认情况下）
>
> 将远程终端提供的token值粘贴进入即可，亦可同时设置密码，从而无需每次输入token。

---

### 6.3 Config

#### 基础设置

> jupyter notebook基本属性的设置都是通过修改配置文件实现的，第一次运行，需要先生成该配置文件。修改基本属性时，找到对应的属性，修改完毕后反注释即可完成更改。

```shell
$ jupyter notebook --generate-config	# 生成配置文件，第一次运行需要
$ vim ~/.jupyter/jupyter_notebook_config.py 	# 编辑配置文件
$ source ~/.jupyter/jupyter_notebook_config.py 	# 同步配置文件
```

> 1. *默认工作路径*，修改`c.NotebookApp.notebook_dir `属性可以修改默认工作路径；
> 2. *默认端口*，修改对应属性可以修改notebook服务默认启用端口；
> 3. *初始密码*，删除token值可以免输入登录；

#### 主题设置

> 以下命令展示了主题设置的基本用法，至于细节上对主题的自定义设置等，过于麻烦不做介绍，如有需要，可自行查找。

```shell
$ pip install jupytertheme	# 安装主题包
$ jt -l						# 打印现有所有主题
$ jt -t <theme_name>		# 选择主题
$ jt -r						# 重置当前主题
```

> 更多jupyter的自定义设置需要修改配置文件，其中jupyter notebook的风格预设路径在` ~/.jupyter/custom` 下，插件的配置文件则（可以通过`jt -r`重置提示得到）在 `/user/.local/share/jupyter/nbextensions`下。
>
> 主题参数修改其下的custom.css以及custom.js文件即可。

---

### 6.4 Plugin

> **切记，不要轻易在base环境下载，否则很容易删不干净！**
>
> 在Jupyter Notebook安装插件，需要先安装插件管理工具，整个过程需要安装两个插件，并且每次插件安装完成后，都需要激活该插件。<u>目前以下操作都会装在默认环境下，好像没办法全局安装，尽管去掉了用户符。</u>
>
> 安装`nbextensions`:
>
> ```SHELL
> $ pip install jupyter_contrib_nbextensions 
> $ pip install jupyter_contrib_nbextensions -i https://pypi.tuna.tsinghua.edu.cn/simple		# if no match version
> $ sudo jupyter contrib nbextension install	  # 全局安装
> ```
>
> 安装`nbextensions_configurator`:
>
> ```SHELL
> $ pip install --user jupyter_nbextensions_configurator
> $ jupyter nbextensions_configurator enable	# 全局共享设置
> ```
>
> 重启jupyter，在弹出的主页面里，能看到增加了一个Nbextensions标签页，在这个页面里，选择需要安装的插件即可，如勾选 Hinterland 启用了**代码自动补全**。

