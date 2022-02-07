# git基本操作

## 一、单人操作

### 1.1 创建空的git仓库：git init

> git仓库和项目根路径在一起，用来管理项目

### 1.2 配置git提交的用户名，邮箱

```bash
$ git config user.name 'username'
$ git config user.email 'email'
```

> 如果没有配置，默认使用：home/.gitconfig根目录下的用户值

### 1.3 查看文件状态：git status

> 红色：表示新建文件，或者新修改的文件，目前位于工作区
>
> 绿色：表示文件在暂存区

### 1.4 将工作区代码添加到暂存区（工作区->暂存区）

```bash
$ git add.
$ git add xxx.py
```

### 1.5 将暂存区代码添加到仓库区

```bash
$ git commit	# 编辑注释
$ git commit --amend 	# 修改提交到上一次他
```

### 1.6 将工作区代码添加到仓库区

```bash
$ git commit -am "注释信息"
```

### 1.7 查看版本历史

```bash
$ git log
$ git reflog
```

### 1.8 回退版本

```bash
$ git reset -hard HEAD
$ git reset -hard 版本号
```

> HEAD（当前指针）表示当前最新版本
>
> HEAD^或 HEAD-1表示当前最新版本的上一个版本
>
> HEAD^^或HEAD-2当前最新版本的前两个版本

### 1.9 撤销工作区，暂存区修改

撤销工作区：

```bash
$ git checkout filename # 如果不指定文件名字则默认全部文件
```

撤销暂存区：

```bash
$ git reset HEAD filename # (暂存区-工作区)
$ git checkout filename
```

> 仓库区代码不能撤销

### 1.10 版本对比

```bash
$ git diff HEAD HEAD^ -- xxx.py
```



## 二、多人开发

### 2.1 clone项目到本地

```bash
$ git clone 项目地址
```

### 2.2 推送项目到远程仓库

```bash
$ git push
```

### 2.3 配置是否输入登录密码信息

```bash
$ git config --global credential.helper cache 十五分钟有效期
$ git config credential.helper 'cache --timeout==3600'一个小时有效期
$ git config --global credential.helper store长期有效
```

### 2.4 拉取远程最新代码到本地

```bash
$ git pull
```

## 三、冲突

### 容易冲突的操作方式：

> 1. 多人同时操作同一个文件
> 2. 一个人一直写不提交
> 3. 修改之前不更新最新代码
> 4. 提交之前不更新最新代码
> 5. 擅自修改他人代码

### 减少冲突的操作方式

> 1. 先pull再修改，修改完立即commit和push
> 2. 一定要确保自己修改的文件是最新版本
> 3. 各自开发各自的模块
> 4. 如果要修改公共文件一定要先确认有没有人正在修改
> 5. 下班前一定要提交代码，上班第一件事拉取最新代码
> 6. 一定不要擅自修改他人代码

## 四、标签

### 4.1 设置本地标签

```bash
$ git tag -a 标签名 -m "标签描述"
```

### 4.2 推送本地标签到远程

```bash
$ git push origin 标签名
```

### 4.3 删除本地标签

```bash
$ git tag -d 标签名
```

### 4.4 删除远程标签

```bash
$ git push origin --delete tag 标签名
```

## 五、分支

分支作用：

1、碰到难题

2、新同事

### 5.1 查看当前分支

```bash
$ git branch
```

### 5.2 创建本地分支，并切换到指定分支

```bash
$ git checkout -b 分支名
```

### 5.3 推送本地分支到远程

```bash
$ git push -u origin 分支名
```

### 5.4 切换分支

```bash
$ git checkout master /dev
```

### 5.5 合并子分支到主分支

```bash
$ git merge 分支
```



# git扩展命令

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

| 参数      | 功能         |
| --------- | ------------ |
| --oneline | 单行显示     |
| --graph   | 以线图显示   |
| --all     | 显示所有分支 |



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

用法

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

![图片](E:\工具\Typora\Temp\640)

用法

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



# 大文件操作

## Getting Started

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

## Git LFS is an open source project

To file an issue or contribute to the project, head over [to the repository](https://github.com/git-lfs/git-lfs?utm_source=gitlfs_site&utm_medium=repo_link&utm_campaign=gitlfs) or read our [guide to contributing](https://github.com/git-lfs/git-lfs/blob/main/CONTRIBUTING.md?utm_source=gitlfs_site&utm_medium=contributing_link&utm_campaign=gitlfs).

If you're interested in integrating Git LFS into another tool or product, you might want to read the [API specification](https://github.com/git-lfs/git-lfs/blob/main/docs/api/README.md?utm_source=gitlfs_site&utm_medium=api_spec_link&utm_campaign=gitlfs) or check out our [reference server implementation](https://github.com/git-lfs/lfs-test-server?utm_source=gitlfs_site&utm_medium=reference_servedr&utm_campaign=gitlfs).
