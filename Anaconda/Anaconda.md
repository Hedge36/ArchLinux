 

# Anaconda 使用教程(linux)

> 以下命令基于Terminal而非anaconda prompt窗口。

进入环境后，可通过python进入相应环境，在随后的(env)中显示有环境名称。

## 1. 频道设置

```bash
$ conda config --add channels url			# 添加镜像源
$ conda config --set show_channel_urls yes	# 设置搜索时显示通道地址
$ conda config --show channels				# 显示添加的镜像源
$ conda config --remove channels url		# 删除已添加的镜像源
$ conda config --remove-key channels		# 还原镜像源设置
```

镜像源地址

| Url                                                          | Description  |
| ------------------------------------------------------------ | ------------ |
| https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/ <br />https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/<br />https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/ | 清华镜像源   |
| https://mirrors.aliyun.com/pypi/simple/                      | 阿里云镜像源 |
| https://pypi.mirrors.ustc.edu.cn/simple/                     | 中科大镜像源 |
| https://pypi.douban.com/simple/                              | 豆瓣镜像源   |



## 2. 环境操作

> 也可以通过anaconda-navigator进行调整。cli下命令如下：

```bash
# 查看现有虚拟环境
$ conda env list
$ conda info -e

# 创建新的虚拟环境
$ conda create -n <env_name> python=3.8	# 默认为当前版本

# 激活与关闭虚拟环境
$ conda activate <env_name>
$ conda deactivate        # 不用接环境名

# 删除虚拟环境或某个包
$ conda remove -n <env_name> --all	# 删除虚拟环境
$ conda remove --name <env_name>  <package_name>	# 删除环境中的某个package
```



## 3. 更新操作

```bash
$ conda update conda	# 更新conda
$ conda update --all	# 更新anaconda所有库
$ conda update anaconda	# 更新anaconda
$ conda install spyder=1.0.0	# 更新spyder
```



## 4. Jupyter

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



### 2. Notebook Sever

可以通过以下命令启动Jupyter本地服务。

```bash
$ jupyter notebook 					# Open notebook
```

一般情况下，默认内核为python3（base），其他虚拟环境需要另外加载，依照以下操作即可，其中`envname`为需要加载的虚拟环境名称。

```bash
$ conda activate envname
$ conda install ipykernel	# 如果已经在vscode上运行过，则已安装
$ python -m ipykernel install --name envname	# 不支持-n短命令
```

