#  Command

## 1. Tutor

> Enter `vimtutor` to read tutor of vim.
>



## 2. Mode

`x` for delete mode (just delete one character one time)

`i` for insert mode

`A` for append mode

> NOTE:  `a`, `i` and `A` all go to the same Insert mode, the only difference is where the characters are inserted (with `a` end of word, `i` current character, `A` end of line).



## 3. Line and Word Command

### Forward command

> `w` for cursor to forward to the start of next word.
>
> `e` for cursor to forward to the end of next word.
>
> `0` for back to the start of line and `$` for end.
>
> `^` for the first non space character.

### Delete command

`d` for deletion command followed motion(seen at the bottom right corner)

> `dw` for delete a word until the start of the next word, excluding its first character.
>
> `de` for delete to the end of current word(the cursor refer to), including the last character.
>
> `d$` for delete from cursor the end of the line, including the last character.
>
> `dd` for delete whole line

### Undo command

> Press `u` to undo the last commands, `U` to fix a whole line, and `Ctrl+R` to redo the command.

### Input command

> Type `p` to put previously delete text after the cursor(next line).

### Replace command

> Type `rx` to replace the character at the cursor with x. 

Move the cursor to the error and type r into replace mode, then enter the charater you want to use to replace.

**Or**

> Type a capital  `R`  to replace more than one character. 

Replace mode is like Insert mode, but every typed character deletes an
existing character.

### Change command

> Type `ce` to change until the end of a word and `cc` to whole line.

Move the cursor th the error you want to correct, then type ce to change word until the end of the current word, at the same time, places you in Insert mode.

**Notes: The usage of c command is almost the same as d command.**

### Command Count

**Use a count for a motion to operate several times.** Just like command following:

`2e` means move the cursor to the end of the third word.

In concrete, use expression like `times forward-operation` , `d times delete-motion` and

`times dd`



## 4. File Command

### Location and State

> Type `Ctrl+G` to show your location in the file and the file status. Type `G` to move to a line in the file.

Hold down the Ctrl key and press  g .  We call this CTRL-G. A message will appear at the bottom of the page with the filename and the
position in the file.You may see the cursor position in the lower right corner of the screen. This happens when the 'ruler' option is set (see  :help 'ruler'  )
                

> Press  `G`  to move you to the bottom of the file.
>
> Type  `gg`  to move you to the start of the file.
>
> Type `NumberG` to move the cursor to the line you specified.

### Search command

> Type `/` followed by a pharse to search for the phrase.

1. In Normal mode type the  “`/`”  character followed characters you search for;

  2. To search for the same phrase again, simply type  `n` .

     To search for the same phrase in the opposite direction, type  `N` .

  3. To search for a phrase in the backward direction, use  `?`  instead of  `/` .

  4. To go back to where you came from press  `CTRL-O` , repeat to go back further.  `CTRL-I` goes forward.

### Matching command

> Type `%` to find a matching ),], or }(Placing cursor on [ to search matching]). Useful in debugging.

### Subtitude command

> Type `:s/old/new/g` to substitude “new” for “old”. Flag `/g` means subtitude all occurrences in the line

More operation see:

`:#,#s/old/new/g`		To change every occurrence of a character string between two lines,where #,# are the line numbers of the range
of lines where the substitution is to be done.

`:%s/old/new/g`			to change every occurrence in the whole file.

`:%s/old/new/gc`			to find every occurrence in the whole file,
with a prompt whether to substitute or not.

### Save command

> To save the changes made to the text, type `:w` filename.

First, you cantype  :!dir  or  :!ls  to get a listing of your directory, then choose a filename that does not exist yet to save as. And if you want to save at current file, just ignore filename. Additionally, you can add other operation at the same time like “:wq” to save and quit.

### Selection save command

> To save part of the file, type  `v  motion  :w filename`.

    1. Move the cursor to this line, then press  `v`  and move the cursor to the end item below you want(That means place you in Visual selection, then you can select words through command v). Next press the  “:”, with `:'<,'>` appearing at the bottom of the screen.  
    2. Now type `w filename` to save as (And in fact, you can type command else like `d` to delete selection).

### Merge command

> To insert the contents of a file, type  `:r filename`.

Place the cursor just above this line, and retrieve your file using the command   `:r filename` where filename is
the name of the file you used.
The file you retrieve is placed below the cursor line.

NOTE:  You can also read the output of an external command.  For example,
`:r !ls` reads the output of the ls command and puts it below the cursor.

## 5. More Command

### External command

> Type  `:!`  followed by an external command to execute that command.

1.  Type `:!` to execute external command, with `!` (exclamation point) character.  This allows you to
          execute any external shell command.
  2. As an example type   ls   following the ! and then hit <ENTER>.  This
     will show you a listing of your directory, just as if you were at the
     shell prompt.  Or use  :!dir  if ls doesn't work.

NOTE:  It is possible to execute any external command this way, also with
arguments.

### Open command

>
> Type `O` to open a line below the cursor and place you in Insert mode, `O` to above. 

### Copy and Paste command

> Use the  `y`  operator to copy text and  `p`  to paste it.

Use Visual mode to select " item.", yank it with  `y` , move to the end of
the next line with  `j$`  and put the text there with  `p`.

NOTE: You can also use  `y`  as an operator:  `yw`  yanks one word,
`yy`  yanks the whole line, then  p  puts that line.

### Set option command

> Set an option so a search or substitute ignores case.

Typing `":set xxx"` sets the option "xxx".  Some options are:
        

| Option            | Description                              |
| ----------------- | ---------------------------------------- |
| 'ic','ignorecase' | Ignore upper/lower case when searching   |
| 'is','incsearch'  | Show partial matches for a search phrase |
| 'hls','hlsearch'  | highlight all matching phrases           |

You can either use the long or the short option name and use “no” like “noic” to close it.

### Use the on-line help system

> Vim has a comprehensive on-line help system.  To get started, try one of
> these three:

1. press the <HELP> key (if you have one)
2. press the <F1> key (if you have one)
3. type   :help

Read the text in the help window to find out how the help works.
Type Ctrl-W to jump from one window to another.
Type :q to close the help window.

You can find help on just about any subject, by giving an argument to the
 ":help" command, just like `help c_CTRL-D`
, `:help insert-index` , `:help user-manual`.

### Create startup script

> Vim has many more features than Vi, but most of them are disabled by default. To start using more features you have to create a "vimrc" file.

  1. Start editing the "vimrc" file.  This depends on your system:
        :e ~/.vimrc
        
  2. Now read the example "vimrc" file contents:
        :r $VIMRUNTIME/vimrc_example.vim


The next time you start Vim it will use syntax highlighting.
You can add all your preferred settings to this "vimrc" file.
  For more information type  :help vimrc-intro

### Completion

> Command line completion with CTRL-D and <TAB> 

NOTE:  Completion works for many commands.  Just try pressing CTRL-D and <TAB>.  It is especially useful for  :help .
