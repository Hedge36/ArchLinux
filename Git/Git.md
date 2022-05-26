# git基本操作

## 1. 基本配置

> git基本配置分为3个级别，系统(system)、全局(global)及本地(local)，分别作用于该系统上的全部用户，当前用户以及当前仓库。
>
> git的全部设置可以通过以下命令进行查看，查看完毕后，可根据相应的属性进行修改。如果无私人账户及私人电脑，不推荐使用全局配置。

```bash
$ git config --list		# 查看本地设置
$ git config --global --list		# 查看全局设置
$ git config --system --list	 	# 查看系统设置
$ git config --global user.name "name"		# 设置全局使用用户名
```

> 对于任意一个用户，绑定`user.name`和`user.email`是必要的。如果没有配置，默认使用 `home/.gitconfig`根目录下的用户值。



## 2. 新建仓库

> git新建仓库包括以下两种方式，实际上，两种方式都需要现在云端github先创建仓库，唯一不同的是后期本地仓库的远程连接方式。

### 1.1 本地新建

> 本地新建仓库的方法比较麻烦，需要现在云端创建仓库后，与本地的仓库文件夹远程连接，具体方法如下，这种方法适合将本地文件夹直接改成一个仓库。

```shell
$ cd path	# 跳转到目录下
$ git init	# 初始化仓库
$ git remote add <name> <"CLONE-URL">		# 连接到云端仓库<name>分支
$ git checkout -b dev	# 创建并切换至分支dev
$ git push origin dev	# 将本地分支dev提交至远程仓库
```

### 1.2 云端新建

> 云端新建仓库的方式比较简单，即在云端新建后，可直接通过Terminal命令直接clone到本地即可，这种方法适合重新建立一个空仓库。

```bash
$ git clone <CLONE-URL>	# 下载远程仓库并且本地分支名为master
$ git clone -b <branch_name> <CLONE-URL>	# 下载远程仓库并且本地分支名为name
```



## 3. 下载仓库

> 下载仓库方法很多，一般而言使用github desktop（windows）或者git clone即可。

```bash
$ git clone <CLONE-URL>
```



## 4. 分支管理

> 分支是git一大特色，常用于解决现有难题或用于提供不同版本。通过checkout命令可以调整当前分支指针，以切换到不同的分支。

#### 4.1 查看/新建分支

```bash
$ git branch	# 查看本地分支
$ git branch -a	# 查看所有分支
```

#### 4.2 切换分支

```bash
$ git checkout <branch-name>	# 切换到分支
$ git checkout -b <branch-name>	# 创建并切换到分支
```

#### 4.3 删除分支

```shell
$ git branch -D <branch_name>	# 删除本地分支
$ git push origin --delete branch	# 删除远程分支
```

#### 4.4 **关联远程分支**

> *<u>origin为远程仓库（Github）的标识</u>*，意为本地修改提交到的分支对象，使用git clone下载时，会自动跟踪到远程仓库，本地初始化时，需要手动设置，否则将会创建新的分支提交。
>
> ==一般情况下，本地分支与跟踪的远程分支名应该相同！==

```bash
$ git remote add <name> <"url">		# add first
$ git branch --set-upstream-to=origin/<branch-name>	<local_branch_name>
# 设置本地分支追踪到远程分支
$ git branch -u origin/<branch-name>	# 将当前分支跟踪到远程分支
$ git branch -vv 	# 查看当前分支追踪情况
```

#### 4.5 合并分支

> 当分支完成测试功能，能够正常使用时，可以将测试分支合并到主支。

```bash
$ git merge <branch-name>	# 合并分支到当前分支
```

#### 4.6 重命名分支

> 当分支名冲突或名字不好听时，可以对分支名进行重命名，其中，对当前分支重命名时可以省略<old_name>参数。

```bash
$ git branch -m <old_name> <new_name>	# 重命名分支
```



## 5. 仓库管理

> 仓库文件分为3个区域，工作区(working)、暂存区(staging)和仓库区(history)，工作区即为本地工作环境，暂存区为本地仓库，仓库区为远程仓库，第一次通过add命令将文件从本地工作区提交至本地仓库暂时保存，随后通过commit命令提交注释至远程仓库。

### 5.1 仓库状态

> 查看当前文件的修改状态，默认情况下不显示忽略文件，红色为工作区修改，绿色为暂存区。

```bash
$ git status [option]	# 查看本地工作区修改
$ git diff HEAD HEAD^ <files>	# 查看两个版本的差异
```

### 5.2 提交修改

#### 工作区

```bash
$ git add.		# 提交全部修改	
$ git add <files-name>	# 提交文件修改
```

#### 暂存区

> 注释为每次提交的概括，用于区分不同的版本，注释规范参见文档`commit_norm.md`。

```bash
$ git commit	# 编辑注释
$ git commit --amend 	# 修改提交到上一次他
```

#### 仓库区

```bash
$ git push		# 提交代码到仓库区
```

### 5.3 提交日志

```bash
$ git log		# 查看提交日志
$ git reflog	# 查看操作日志
```

### 5.4 回退版本

> Head表示当前指针，通过使用checkout调整指针所在版本号进行版本的回退

```bash
$ git checkout <>
$ git reset -hard HEAD	# 
$ git reset -hard 版本号
```

> HEAD（当前指针）表示当前最新版本
>
> HEAD^或 HEAD-1表示当前最新版本的上一个版本
>
> HEAD^^或HEAD-2当前最新版本的前两个版本

### 5.5 更新版本

> 更新版本有两种方式，一般采用pull，但实际上，由于pull隐藏了更新具体过程，可能会导致一些问题，更加安全的方式是通过fetch和merge方法进行更新。

```bash
# --- Method1 ---
$ git pull	# 强制合并

# --- Method2 ---
$ git fetch	# 获取修改 
$ git merge	# 合并修改
```

### 5.6 撤销修改

#### 撤销工作区

> 撤销工作区修改有两种方式，任意一直均可。

```bash
$ git checkout <filename> # 如果不指定文件名字则默认全部文件
$ git restore <filename>
```

#### 撤销暂存区

> 同两种

```bash
$ git reset HEAD filename # (暂存区-工作区)
$ git checkout filename
```

> 仓库区代码不能撤销



## 6. 冲突处理

### 6.1 产生原因

> 冲突的产生源于本地仓库与终端仓库版本差异，git提交时存在版本差异（往往是版本缺失）而无法提交，需要提交者自行处理。
>
> **容易冲突的操作方式**
>
> > 1. 多人同时操作同一个文件
> > 2. 一个人一直写不提交
> > 3. 修改之前不更新最新代码
> > 4. 提交之前不更新最新代码
> > 5. 擅自修改他人代码
>
> **减少冲突的操作方式**
>
> > 1. 先pull再修改，修改完立即commit和push
> > 2. 一定要确保自己修改的文件是最新版本
> > 3. 各自开发各自的模块
> > 4. 如果要修改公共文件一定要先确认有没有人正在修改
> > 5. 下班前一定要提交代码，上班第一件事拉取最新代码
> > 6. 一定不要擅自修改他人代码



## 7. 其他操作

### 7.1 短命令

> git支持独立的短命令设置

```bash
$ git config alias.<alias> "command"

# then using by
$ git <alias>
```

### 7.2 撤销commit

> 写完代码后，我们一般这样
>
> git add . //添加所有文件
>
> git commit -m "本功能全部完成"
>
> 执行完commit后，想撤回commit，怎么办？
>
> 这样凉拌：
>
> git reset --soft HEAD^
>
> 这样就成功的撤销了你的commit
>
> 注意，仅仅是撤回commit操作，您写的代码仍然保留。
>
>  
>
> 说一下个人理解：
> HEAD^的意思是上一个版本，也可以写成HEAD~1
>
> 如果你进行了2次commit，想都撤回，可以使用HEAD~2
>
> 至于这几个参数：
>
> --mixed 
> 意思是：不删除工作空间改动代码，撤销commit，并且撤销git add . 操作
> 这个为默认参数,git reset --mixed HEAD^ 和 git reset HEAD^ 效果是一样的。
>
> --soft  
> 不删除工作空间改动代码，撤销commit，不撤销git add . 
>
> --hard
> 删除工作空间改动代码，撤销commit，撤销git add . 
>
> 注意完成这个操作后，就恢复到了上一次的commit状态。

### 7.3 标签

#### 设置本地标签

```bash
$ git tag -a 标签名 -m "标签描述"
```

#### 推送本地标签到远程

```bash
$ git push origin 标签名
```

#### 删除本地标签

```bash
$ git tag -d 标签名
```

#### 删除远程标签

```bash
$ git push origin --delete tag 标签名
```





# Sgit协作开发

### 2.1 配置是否输入登录密码信息

```bash
$ git config --global credential.helper cache 十五分钟有效期
$ git config credential.helper 'cache --timeout==3600'一个小时有效期
$ git config --global credential.helper store长期有效
```





# 参考手册

## 1. git push

> 将更改推送到存储库。用法如下：

```bash
$ git push -u <short_name> <your_branch_name>
```

## 2. git push --set-upstream

> 在使用`git push`之前，我们应该先设置好`origin`和`upstream`。下面是设置`upstream`的命令。用法如下：

```bash
$ git push --set-upstream <short_name> <branch_name>
```

## 3. git fetch

> 当需要下载其他团队成员的更改时，就得使用`git fetch`。
>
> 此命令会下载有关提交、引用等的所有信息，因此你可以在将这些更改应用于本地存储库之前对其进行检查，但**不会更新本地内容**，你需要通过合并命令来实现。用法如下：

```bash
$ git fetch
$ git merge
```

## 4. git pull

> `git pull`命令下载仓库最新内容，并立即用最新的内容更新本地存储库，**当出现冲突时，默认使用最新文件覆盖本地文件**。用法如下：

```bash
$ git pull <remote_url>
```

## 5. git stash

> 此git命令会临时存储已修改的文件，往往用于合并冲突处理。你可以使用以下Git命令处理stash工作, stash 用法有很多，比如save，push，pop，clear等，需要使用可以查阅[stash 命令](https://git-scm.com/docs/git-stash)，用法如下

```bash
$ git stash
```

可以使用以下命令查看所有stash

```bash
$ git stash list
```

如果你需要应用stash到分支，那就使用`apply`

```bash
$ git stash apply
```

## 6. git log

> 在`git log`的帮助下，你可以看到所有之前的提交，并且最近的提交出现在最前面，默认情况下，它将显示当前已检出分支的所有提交。用法如下：

```bash
$ git log
```

此外还有以下参数：

| 参数      | 功能                             |
| --------- | -------------------------------- |
| --oneline | 单行显示                         |
| --graph   | 以线图显示                       |
| --all     | 显示所有分支                     |
| --stas    | 显示日志具体修改信息             |
| --patch   | 显示日志具体修改信息及文档原文件 |

## 7. git shortlog

> `git shortlog`命令会显示来自`git log`命令的摘要。如果你只对简短的摘要感兴趣，那么此命令就非常有用了。这个命令有助于查看谁处理了什么，因为它对作者及其提交进行了分组。

```bash
$ git shortlog
```

## 8. git show

> 与`git log`相比，此命令将显示有关特定提交的详细信息。

```bash
$ git show <your_commit_hash>
```

## 9. git rm

> 有时你需要从代码库中删除文件，在这种情况下，可以使用`git rm`命令。它可以从索引和工作目录中删除跟踪的文件。

```bash
$ git rm <your_file_name>
```

## 10. git merge

> `git merge`可帮助将来自两个分支的更改集成到单个分支中。

```bash
$ git merge <branch_name>
```

此命令会将`<branch_name>`合并到当前你选择的分支中。

## 11. git rebase

> `git rebase`类似于`git merge`命令。它把两个分支集成到一个分支中，但有一个不一样的地方：`git rebase`命令将会重写提交记录。
>
> 当你有多个私有分支合并到单个分支时，应使用`git rebase`命令。它将使得提交历史成为线性的。

```bash
$ git rebase <base>
```

## 12. git bisect

`git bisect`命令可帮助查找糟糕的提交。

用法

i）启动`git bisect`

```bash
$ git bisect start
```

ii）让`git bisect`知道什么是好的提交

```bash
$ git bisect good a123
```

iii）让`git bisect`知道什么是糟糕的提交

```bash
$ git bisect bad z123
```

通过`git bisect`，只要几分钟你就可以缩小问题代码的范围。

## 13. git cherry-pick

`git cherry-pick`是一个蛮有用的命令，允许你从任意分支中选择任意提交并将其应用于其他任意分支。

用法

```bash
$ git cherry-pick <commit-hash>
```

`git cherry-pick`不会修改存储库的历史记录；相反，它会添加到历史记录。

## 14. git archive

`git archive`命令会把多个文件合并为单个文件。就好像zip实用程序一样，所以你可以提取存档文件以获取单个文件。

用法

```bash
$ git archive --format zip HEAD > archive-HEAD.zip
```

它将创建当前修订的zip存档。

## 15. git pull --rebase

在大多数情况下，当你使用`git pull`时，你需要重新设置基准（并且不进行合并）。

此时，你就可以使用此选项。

用法

```bash
$ git pull --rebase
```

这将帮助保持干净的历史记录。另外，还可以避免多次合并。

## 16. git blame

如果你需要逐行检查任意文件的内容，则需要使用`git blame`命令。它可以帮助确定是谁对文件进行了更改。

用法

```bash
$ git blame <your_file_name>
```

## 17. git tag

在Git中，标签很有用，你可以使用它们来管理发布。你可以将`git tag`视为不会改变的分支。尤其是要公开发布的时候，则更为重要了。

用法

```bash
$ git tag -a v1.0.0
```

## 18. git verify-commit

`git verify-commit`命令将检查gpg签名。GPG，GNU Privacy Guard，是sign文件中使用的工具，包含签名。

用法

```bash
$ git verify-commit <commit>
```

## 19. git verify-tag

可以以同样的方式确认标签。

用法

```bash
$ git verify-tag <tag>
```

## 20. git diff

大多数情况下，在提交或推送之前，你需要比较两个git文件或分支。用这个命令就方便多了。

用法

i）将工作区与暂存区内容进行比较：

```bash
$ git diff HEAD <filename>
```

ii）比较两个分支：

```bash
$ git diff <source branch> <target branch>
```

## 21. git citool

`git citool`是Git提交的图形化替代。

```bash
$ git citool
```

## 22. git mv

重命名git文件。接受两个参数，源文件名和目标文件名。

用法

```bash
$ git mv <old-file-name> <new-file-name>
```

## 23. git clean

你可以使用`git clean`命令处理未跟踪的文件。可以使用此命令从工作目录中删除所有未跟踪的文件。如果要处理跟踪的文件，则需要使用`git reset`命令。

用法

```bash
$ git clean
```

## 24. git help

Git中有许多命令，如果你需要其他命令的帮助，则可以随时在终端上使用`git help`。

用法

```bash
$ git help <git_command>
```

## 25. git whatchanged

此命令的作用与`git log`相同，但为原始格式。并且由于历史原因，它也是git的一份子。

用法

```bash
$ git whatchanged
```





# Large File Storage(LFS)

## 1. Getting Started

[Download](https://github.com/git-lfs/git-lfs/releases/download/v2.13.2/git-lfs-windows-v2.13.2.exe) and install the Git command line extension. Once downloaded and installed, set up Git LFS for your user account by running:

```bash
$ git lfs install
```

You only need to run this once per user account.

In each Git repository where you want to use Git LFS, select the file types you'd like Git LFS to manage (or directly edit your .gitattributes). You can configure additional file extensions at anytime.

```bash
$ git lfs track "*.psd"
```

Now make sure .gitattributes is tracked:

```bash
$ git add .gitattributes
```

Note that defining the file types Git LFS should track will not, by itself, convert any pre-existing files to Git LFS, such as files on other branches or in your prior commit history. To do that, use the [git lfs migrate[1\]](https://github.com/git-lfs/git-lfs/blob/main/docs/man/git-lfs-migrate.1.ronn?utm_source=gitlfs_site&utm_medium=doc_man_migrate_link&utm_campaign=gitlfs) command, which has a range of options designed to suit various potential use cases.

There is no step three. Just commit and push to GitHub as you normally would; for instance, if your current branch is named `main`:

```bash
$ git add file.psd
$ git commit -m "Add design file"
$ git push origin main
```

## 2. Git LFS is an open source project

To file an issue or contribute to the project, head over [to the repository](https://github.com/git-lfs/git-lfs?utm_source=gitlfs_site&utm_medium=repo_link&utm_campaign=gitlfs) or read our [guide to contributing](https://github.com/git-lfs/git-lfs/blob/main/CONTRIBUTING.md?utm_source=gitlfs_site&utm_medium=contributing_link&utm_campaign=gitlfs).

If you're interested in integrating Git LFS into another tool or product, you might want to read the [API specification](https://github.com/git-lfs/git-lfs/blob/main/docs/api/README.md?utm_source=gitlfs_site&utm_medium=api_spec_link&utm_campaign=gitlfs) or check out our [reference server implementation](https://github.com/git-lfs/lfs-test-server?utm_source=gitlfs_site&utm_medium=reference_servedr&utm_campaign=gitlfs).

