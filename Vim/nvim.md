#  Chapter1 Basic

## 1. Tutor

> Enter `vimtutor` to read tutor of vim.



## 2. Mode

> There are three mode in vim, Command Mode, LastLine Mode and Insert Mode. Insert mode is to insert content to text. You can place yourself in Insert mode by ways belowed: 
>
> 1. Type `i` for insert mode before cursor, `I` for insert mode at the beginning of the line. 
> 2. Type `a` , `A` for Insert mode after cursor. 
>
> 3. Type `o` to open a line below the cursor and place you in Insert mode, `O` to above. 
> 4. Type `s` to delete current character and place in insert mode, `S` for the whole line.
>
> > **NOTE:  `a`, `i` and `A` all go to the same Insert mode, the only difference is where the characters are inserted (with `a` end of word, `i` current character, `A` end of line).**



## 3. Command Mode

### 3.1 Forward command

#### Line

> `w` for cursor to forward to the start of next word.
>
> `b` for cursor to forward to the start of last word.
>
> `e` for cursor to forward to the end of next word.
>
> `ge` for cursor to forward to the end of last word.
>
> `0` for back to the start of line and `$` for end.
>
> `^` for the first non space character.

#### Page

> `Ctrl+u` for turning back half a page
>
> `Ctrl+d` for turning forward half a page
>
> `Ctrl+f` for turning forward a page
>
> `Ctrl+b` for turning back a page

### 3.2 Delete command

> `d` for deletion command followed motion(seen at the bottom right corner).
>
> For `x` to delete current one character and `X` to delete one before.
>
> > `dw` for delete a word until the start of the next word, excluding its first character.
> >
> > `de` for delete to the end of current word(the cursor refer to), including the last character.
> >
> > `d$` for delete from cursor the end of the line, including the last character.
> >
> > `dd` for delete whole line to move, you can type `p` to put lines after the cursor(next line).

### 3.3 Undo command

> Press `u` to undo the last commands, `U` to fix a whole line, and `Ctrl+R` or `.` to redo the command.

### 3.4 Replace command

> > Type `rx` to replace the character at the cursor with x. 
>
> Move the cursor to the error and type r into replace mode, then enter the charater you want to use to replace.
>
> **Or**
>
> > Type a capital  `R`  to replace more than one character. 
>
> Replace mode is like Insert mode, but every typed character deletes an
> existing character.

### 3.5 Change command

> > Type `ce` to change until the end of a word and `cc` to whole line.
>
> Move the cursor th the error you want to correct, then type ce to change word until the end of the current word, at the same time, places you in Insert mode.
>
> **Notes: The usage of c command is almost the same as d command.**

### 3.6 Copy and Paste command

> > Use the  `y`  operator to copy text and  `p`  to paste it.
>
> Use Visual mode to select " item.", yank it with  `y` , move to the end of
> the next line with  `y$`  and put the text there with  `p`.
>
> NOTE: You can also use  `y`  as an operator:  `yw`  yanks one word,
> `yy`  yanks the whole line, then  `p`  puts that line.
>
> > **Pay attention that** nvim doesn't support system clipboard and register(`+`), if you need that, you need to [configure](https://zhuanlan.zhihu.com/p/419472307) it by yourself. Otherwise, you can only copy and paste in current vim windows!
> >
> > To solve this problem in specified cases like copying whole file, you can archieve your purpose by shell(*xsel is needed*) as followed.
> >
> > ```SHELL
> > $ echo <text> | xsel -i -b	# text input clipboard
> > $ cat <file> | xsel -i -b	# file input clipboard
> > $ xsel -o -b	# xsel output clipboard
> > $ xsel -c		# clear clipboard but malfunction in fact
> > $ xsel -h 	# for help
> > ```

### 3.7 Command Count

> **Use a count for a motion to operate several times.** Just like command following:
>
> In concrete, use expression like `times forward-operation` , `d times delete-motion` and
>
> `times dd`. Just like`2e`, which means move the cursor to the end of the third word.



## 4. File Command

### 4.1 Location and State

> > Type `Ctrl+G` to show your location in the file and the file status. Type `G` to move to a line in the file.
>
> Hold down the Ctrl key and press  g .  We call this CTRL-G. A message will appear at the bottom of the page with the filename and the
> position in the file.You may see the cursor position in the lower right corner of the screen. This happens when the 'ruler' option is set (see  :help 'ruler'  )
>                 
>
> > Press  `G`  to move you to the bottom of the file.
> >
> > Type  `gg`  to move you to the start of the file.
> >
> > Type `NumberG` to move the cursor to the line you specified.

### 4.2 Search command

> > Type `/` followed by a pharse to search for the phrase.
>
> 1. In Normal mode type the  “`/`”  character followed characters you search for;
>
>   2. To search for the same phrase again, simply type  `n` .
>
>      To search for the same phrase in the opposite direction, type  `N` .
>
>   3. To search for a phrase in the backward direction, use `?` instead of `/` .
>
>   4. To go back to where you came from press  `CTRL-O` , repeat to go back further.  `CTRL-I` goes forward.
>
> Type `:noh`or `nohlsearch` to close highlight of search result.

### 4.3 Matching command

> Type `%` to find a matching ), ] or } (Placing cursor on [ to search matching]). Useful in debugging.





# Chapter2 Last line mode

> For Lastline mode, you just need to enter <u>`:`</u>.
>
> At this mode, you can achieve many operation easily.

## 1. External command

> > Type `:!` followed by an external command to execute that command.
>
> 1.  Type `:!` to execute external command, with `!` (exclamation point) character.  This allows you to execute any external shell command.
>   2. As an example type `ls`  following the ! and then hit <ENTER>.  This
>      will show you a listing of your directory, just as if you were at the
>      shell prompt.  Or use `:!dir` if ls doesn't work.
>
> NOTE: It is possible to execute any external command this way, also with
> arguments.
>
> Additionally, you can Enter <kbd>Ctrl+Z</kbd> or `:suspend` to freeze your current file and back to shell to enter your command, finally, you can type `fg` in the shell to forward back the first suspended file or you  can type `%<N>` to draw back the N^th^ suspended windows . **It is worth noting that don't forget to suspend your file, or you will lose all of your buffet.**



## 2. Line Operation Command

### 2.1 Line Operation

> Type `:<n1>,<n2> copy <n3>` to copy line n1-n2 and paste after line n3. 
>
> Similarly, Type `:<n1>,<n2> move <n3>` to move line n1-n2 after line n3.
>
> Type `:<n>/d` to delete line n with multiple lines deleted, type `:<n>g/<string>/d` to delete line with <string> in line n.

### 2.2 Subtitude command

> Type `:s/old/new/g` to substitude “new” for “old”. Flag `/g` means subtitude all occurrences in the line

> More operation see:
>
> `:#,#s/old/new/g`			To change every occurrence of a character string between two lines,where #,# are the line numbers of the range
> of lines where the substitution is to be done.
>
> `:%s/old/new/g`				to change every occurrence in the whole file.
>
> `:%s/old/new/gc`			  to find every occurrence in the whole file,
> with a prompt whether to substitute or not.

### 2.3 Save command

> > To save the changes made to the text, type `:w filename`.
>
> First, you cantype  :!dir  or  :!ls  to get a listing of your directory, then choose a filename that does not exist yet to save as. And if you want to save at current file, just ignore filename. Additionally, you can add other operation at the same time like “`:wq`” or `:x` to save and quit.

### 2.4 Selection save command

> > To save part of the file, type  `v  motion  :w filename`.
>
> 1. Move the cursor to this line, then press  `v`  and move the cursor to the end item below you want(That means place you in Visual selection, then you can select words through command v). Next press the  “:”, with `:'<,'>` appearing at the bottom of the screen.  
> 2. Now type `w filename` to save as (And in fact, you can type command else like `d` to delete selection).

### 2.5 Merge command

> > To insert the contents of a file, type  `:r filename`.
>
> Place the cursor just above this line, and retrieve your file using the command   `:r filename` where filename is
> the name of the file you used.
> The file you retrieve is placed below the cursor line.
>
> NOTE:  You can also read the output of an external command.  For example,
> `:r !ls` reads the output of the ls command and puts it below the cursor.



## 3. Option Command

### 3.1 Set Option

> > Set an option so a search or substitute ignores case.
>
> Typing `":set xxx"` sets the option "xxx".  Some options are:
>
>
> | Option            | Description                              |
> | ----------------- | ---------------------------------------- |
> | 'ic','ignorecase' | Ignore upper/lower case when searching   |
> | 'is','incsearch'  | Show partial matches for a search phrase |
> | 'hls','hlsearch'  | highlight all matching phrases           |
>
> You can either use the long or the short option name and use “no” like “noic” to close it.

### 3.2 Use the on-line help system

> > Vim has a comprehensive on-line help system.  To get started, try one of
> > these three:
>
> 1. press the <HELP> key (if you have one)
> 2. press the <F1> key (if you have one)
> 3. type   :help
>
> Read the text in the help window to find out how the help works.
> Type Ctrl-W to jump from one window to another.
> Type :q to close the help window.
>
> You can find help on just about any subject, by giving an argument to the
>  ":help" command, just like `help c_CTRL-D`
> , `:help insert-index` , `:help user-manual`.

### 3.3 Create startup script

> > Vim has many more features than Vi, but most of them are disabled by default. To start using more features you have to create a "vimrc" file.
>
>     1. Start editing the "vimrc" file.  This depends on your system:
>     :e ~/.vimrc
>                    
>     2. Now read the example "vimrc" file contents:
>     :r $VIMRUNTIME/vimrc_example.vim
>
> The next time you start Vim it will use syntax highlighting.
> You can add all your preferred settings to this "vimrc" file.
>   For more information type  :help vimrc-intro

### 3.4 Completion

> > Command line completion with CTRL-D and <TAB> 
>
> NOTE:  Completion works for many commands.  Just try pressing CTRL-D and <TAB>.  It is especially useful for  :help .





# Chapter3 Advanced

## 1. Views

> Use `:sp` to split the window horizonally or `vsp` vertically, then you can get two same file windows, use `:e filename` to open another file, use `Ctrl+W` to switch to windows mode, and insert one more `w` in command mode to switch to another file. So then, you can finish copy and paste in two different file.
>
> Last, use `Ctrl+w` in command mode with `c` to close current file window.



## 2. Mark

> use `m<name>[a-z]` (**without `:`**) to create a mark with name [a-z], then you can index its' accurate position(with columns) with ``<name>` and `'<name>` for line instead.
>
> to show all marks, you can type command `:marks` with markname for mark's detail and `:delmarks <names> `  to delete one or more marks with `!` all marks. 
>
> Additionally, there are some default marks, like 
>
> | Mark  | Denotion                   |
> | ----- | -------------------------- |
> | `.`   | Position edited last time  |
> | `0-9` | Files edit recently        |
> | `^`   | Position inserted recently |
> | `'`   | Position jump last time    |
> | `"`   | Position exit last time    |
> | `[`   | Beginning of last modify   |
> | `]`   | End of last modify         |



## 3. Tab

> Vim supports operating multiple tab. 
>
> Firest, you can type `vim -p <filelist>` to open file(s) to be edited. Additionally, you can open multiple tabs in vim view by typing `:tabnew <filelist>`.
>
> Then, here are some simple command and to operate tabs. 
>
> | Command | Function                           |
> | ------- | ---------------------------------- |
> | `:tabc` | Close the tab opening current      |
> | `:tabo` | Close all tabs besides current tab |
> | `:tabs` | View all tabs opening              |
> | `:tabp` | Switch to previous tab             |
> | `:tabn` | Switch to next tab                 |
>
> You can also switch tab by typing shortcut `gt` to previous tab and `gT` to next. 



## 4. Filetree

> Type `:Ex` open file manager in current directory, and you can open file through Enter. By default, It will open in the sidebar. If you want open it in the horizon view, you can type `:Sex`.
>
> And type `:ls` to show current buffer.





# Chapter4 Plugin

## 1. Vim-Plug

> 自从 Vim 8 以后，包管理器变得不那么有用了，但是一些用户仍然喜欢它们，因为它们能够自动更新一些插件。有几个包管理器可供选择，并且它们各不相同，但是 [vim-plug](https://github.com/junegunn/vim-plug) 有一些很棒的特性和最好的文档，这使我们很容易开始并在以后深入研究。

### 1. Install

> 安装 vim-plug，以便它在启动时自动加载：

```shell
$ curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
  https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

> 创建一个 `~/.vimrc` 文件（如果你还没有这个文件），然后输入以下文本：

```text
call plug#begin()
Plug 'preservim/NERDTree'
call plug#end()
```

> 每次要安装插件时，都必须在 `plug＃begin()` 和 `plug＃end()` 之间输入插件的名称和位置（上面以 NERDTree 文件管理器为例）。如果你所需的插件未托管在 GitHub 上，你可以提供完整的 URL，而不仅仅是 GitHub 的用户名和项目 ID。你甚至可以在 `~/.vim` 目录之外“安装”本地插件。
>
> 最后，启动 Vim 并提示 vim-plug 安装 `~/.vimrc` 中列出的插件，等待下载即可。

```text
:PlugInstall
```

### 2. Config

> 与vim有些差异，nvim的配置文件位于`.config/nvim/init.vim`

### 3.使用计划

> 1. Nerdtree的使用；
> 2. 



![img](/home/hedge/Tools/typora_images/6635185-d6cf5493a68e9499.png)



## 2. Markdown

### 1. Vim-markdown

#### Description

> [vim-markdown](https://github.com/plasticboy/vim-markdown) 是一个Markdown语法高亮插件。其提供了针对Markdown的语法高亮，段落折叠，查看目录，段间跳转等功能，相当好用。
>
> 其具体配置方法参考github仓库`README.md`。

#### Install

```vim
"安装插件
Plug 'godlygeek/tabular' "必要插件，安装在vim-markdown前面
Plug 'plasticboy/vim-markdown'
"
```

#### Usage

##### Manual

```vim
"查看所有配置建议
:help vim-markdwon
```

##### Command

```vim
[[ "跳转上一个标题
]] "跳转下一个标题
]c "跳转到当前标题
]u "跳转到副标题
zr "打开下一级折叠
zR "打开所有折叠
zm "折叠当前段落
zM "折叠所有段落
:Toc "显示目录
```

由于我们还会使用到Latex数学公式，所以可以在配置文件中加上

```vim
let g:vim_markdown_math = 1
```

来高亮数学公式。



### 2. Markdown-preview.nvim

#### Description

> [markdonw-preview.nvim](https://github.com/iamcco/markdown-preview.nvim)（Neovim）可以通过浏览器实时预览Markdown 文件。并可以借助浏览器的打印功能导出PDF文档，同时附带了Latex预览，Mermaid甘特图，Plantuml UML图等等一系列功能。
>
> 详情配置见github仓库说明。

#### Install

```vim
" 安装插件
Plug 'iamcco/markdown-preview.nvim'
```

#### Command

```vim
" 打开/关闭预览
:MarkdownPreviewToggel

" 指定浏览器路径
let g:mkdp_path_to_chrome = "path/of/chrome"

" 指定预览主题，默认Github
let g:mkdp_markdown_css=''
```

