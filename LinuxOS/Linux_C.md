# Chapter1 概述

## 1. Linux C与C

> Linux C与C语言学习的本质区别在于，C语言学习的主要内容包括C的语法和标准C的库函数，而Linux下的C开发课程学习的是Linux系统调用，也就是使用Linux系统提供的函数，又叫内核函数。系统调用属于底层调用，适合硬件编程。
>



```Shell
$ gcc [option] parameters
```

| Option | Description                        |
| ------ | ---------------------------------- |
| -o     | to specify the name of file        |
| -g     | generate exe with debug info       |
| -c     | compile only and do not link       |
| -E     | preprocess only                    |
| -S     | translate to compilation by C.     |
| -l     | Link to library(Remove `.b`/`.so`) |
| -L     | Path of library to lib             |



```Shell
$ gdb [option]
```

### 基本流程

```Shell
$ gcc test.c
$ gdb a.out		# 将可执行文件缓冲至gdb
(gdb) start		# 开始调试
(gdb) n			# 逐行测试
(gdb) step		# 执行一行代码
(gdb) backtrace		# 查看函数调用栈帧
(gdb) info locals	# 查看当前栈帧局部变量
(gdb) frame			# 选择栈帧，再查看局部变量
(gdb) print			# 打印变量值
(gdb) finish		# 运行到当前函数返回
(gdb) set var <name>=<value>	# 修改变量值
(gdb) list <nrows>	# 列出源代码
(gdb) break	<num>		# 在行<num>处设置断点 
(gdb) continue			# 连续运行
(gdb) info breakpoints <number>		# 查看断点
(gdb) delete breakpoints <number>	# 删除断点
(gdb) disable/enable breakpointe <number>	# 启用断点
(gdb) break <breakpoint> if <expression>	# 满足条件时启用断点
(gdb) run		# 从头开始执行
(gdb) watch input	# 设置观察点
(gdb) infor watchpoints		# 查看设置的观察点
(gdb) x/<num>b input		# 打印前<num>个字节组的存储器内容
(gdb) info registers		# 打印寄存器内容
(gdb) x/<num> $esp			# 查看内存中的前<num>个变量
```



### 基本命令

|      |      |
| ---- | ---- |
|      |      |
|      |      |
|      |      |

