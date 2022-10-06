
# 为什么非要用Terminal

- 许多功能在图形界面不提供，只有通过命令行来实现。
- Finder 会隐藏许多你不太会需要的文件，而 Command line 则可以访问所有文件。
- Command line 可以通过 SSH 远程访问你的 Mac 或者 Linux。
- 普通用户可以通过 `sudo` 命令获得 root 用户权限。
- 如果你开启手动输入用户名登陆模式，登陆时在用户名处输入 `>console` 可以直接进入命令行界面。随后你仍然需要登录到一个账户。



如果找不到文件的话，使用comand+shift+.即可显示隐藏文件



## Terminology

- **Command line**: A command-line interface is a way of giving instructions to a computer and getting results back
- **Shell**: A shell is a program that creates a user interface of one kind or another enabling you to interact with a computer
	- **csh**: the C shell, named for similarities to the C programming language
	- **zsh**: the Z shell, an advanced shell named after Yale professor Zhong
	Shao that incorporates features from tcsh, ksh, and bash, plus other
	capabilities
	- **dash**: the Debian Almquist shell, a lightweight shell that’s been around
	for more than two decades, but was not included with macOS until
	Catalina
- **Terminal**: the devices people used to interact with computers back in the days of
monolithic mainframes.



## commands, aruguments  and flags

- **Command**: Commands are straightforward; they’re the verbs of the command line (eventhough they may look nothing like English verbs).
```
pwd
date
```
- **Arguments**: Along with commands (verbs), we have arguments, which you can think ofas nouns

比如你要处理一个文件，需要指定这个文件的名字

```
nano file1
```

- **Flags**: Besides verbs and nouns, we have adverbs! In English, I could say, “Eatcereal quickly!” or “Watch TV quietly.”

ls展示文件，ls a展示所有文件

```
ls
ls -l. (including sizes and dates)
ls -l (note the space before the tag)
ls -l -a == ls -la
ls -l r* # show you only the names of files beginning with the letter r

```

- **syntax**语法: 





# Zsh的食用指北

command + T: 创建mutiple sessions

command + -(period):  取消一个命令












# 需要记住的命令
## man
指南，但读起来真的头大，不推荐用。
```
man command_name
```
例如
```
man cd
man ls
```

## 常用的命令

| 命令 |     作用     | 参数 |
| :--: | :----------: | ---- |
| pwd  | print working directory | -l, |
|  ls    | list directory contents            |  |
|   cd   | change directory             |  |
| which + command | 显示command所使用的文件 |  |
|  |  |  |
|  |  |  |
|  |  |  |
| | |  |



## 组合

- Finder中打开文件路径：defaults write com.apple.finder _FXShowPosixPathInTitle -bool TRUE;killall Finder 
- 





# 关于文件路径的问题
## 绝对路径
反斜杠/开头，例如
```
/Users/nymath # 默认的工作路径
```
- 可以从finder里把文件拖到terminal里进而得到该文件的绝对路径。

- Tab Complete 是 Command line 中最能给你节省时间的特性之一，利用它的自动完成文件、目录名称功能还可以防止输入错误。使用 cd 进入你的 home folder，使用 cd P 命令，然后按下tab按键。可能会听到错误音，因为你的 home folder 内有多个 P 开头的文件夹。再按一次 tab，Terminal 将会为你列出 P 开头的两个文件夹：Public 和 Pictures。按 U，再按 tab，Terminal 则会自动为你补全 Public/。Tab complete 同样会处理那些特殊字符。注意，这会在末尾保留 / 符号，大部分时候这没问题，但如果出错，移除多余的 / 试一试。

- ~在command line中表示默认工作路径

- 



**使用递归命令**
 简单来说，递归命令可以允许命令不执行于一个特定文件，而是指定的路径下的所有文件。大多数命令包含一个 `-r` 或者 `-R` 选项，来设定你想递归地执行这个命令。例如下面的例子，添加 `-R` 后 `ls` 命令的执行方式：`ls -R Public`，这会列出 Public 中的所有文件，若有文件夹，则会继续列出文件夹中的内容



输入open . 可以在finder中打开当前目录

## Macos 的文件结构

## find and locate

```
find ~ -name "*keychain*"
```



# Work with Files and Directories

## Create a File(文件)

touch

```
touch ~/file1.csv
```



- *When supplied with the name a nonexistent file as an argument,*

  *touch* *creates an empty file.*
  
- *When supplied with the name of an existing file or folder as an*

  *argument,* *touch* *updates its modification date to the current date and*

  time, marking it as modified.



## Crete a Directory（名录薄，或者文件夹）

mkdir ("make directory")

```shell
mkdir apples
mkdir ~/apples
```





## Copy a File or Directory

cp

### file

It takes two arguments: the first is the file you want tocopy, and the second is the destination for the copy

```shell
cp ~/Documents/file1 /Users/Shared
cp ~/Documents/file1 /Users/Shared/file1
cp ~/Documents/file1 /Users/Shared/file2
cp file1 file2 file3 /Users/Shared
```

### Directory

You can use the cp command to copy a directory, but you must add the -r(“recursive”) flag.

```shell
cp -r apples ~/Documents
```



## Move or Rename

mv, rm, rmdir

```shell
mv /Users/jk/Documents/file1 /Users/Shared
mv file1 file2 #rename
mv file1 Documents/file2 # move and rename
mv file1 file2 file3 /Users/Shared # move multiple files
```



## Delete

Rm,

 rmdir #

```shell
rmdir emptyfile # 仅仅适用于空文件夹
rm -r apples # 需要用到recursive
```

alias, symbolic link： 快捷方式





# Work with Programs

To run a program, your shell must be able to find it. 

By default, your PATH includes all of the following directories:

```shell
/bin
/sbin
/usr/bin
/usr/local/bin
/usr/sbin
```

A program in any of these locations is said to be “in your PATH.”

insert *ls -l /bin* toget an idea of the hundreds of built-in programs and where they’re located.

Also, enter echo $PATH to see the current contents of your PATH.

```shell
echo $PATH
/opt/homebrew/bin
/opt/homebrew/sbin
/usr/local/bin:
/usr/bin:
/bin:
/usr/sbin:
/sbin:
/Library/TeX/texbin:
/Library/Apple/usr/bin
```



In practice, we need to expend the size of $PATH. (Modify your PATH)



## Run a Program

To summarize, you can run a program in any of three ways, depending onwhere the program is located, your current position in the directory structure, and what’s in your PATH:

- **Absolute path**:  e.g. /usr/bin/programfile
- **In the current directory**:  ./programfile
- **In your Path**:  simply enter the program's name, e.g., less, mkdir, man.
- 



## Run a Script



A shell script is a series of instructions interpreted, or run, by the shell itself. So, a shell script could consist of little more than a list of commands, just asyou would type them manually in a Terminal window. 

In addtion, you should remember that shell scripts usually have an extension of .sh.

Perl scripts: .pl

PHP scripts: .php

Python script: .py



Regardless of a script’s extension, it’s considered good programmingpractice to include the name and location of the interpreter that shouldprocess it on the first line of the script. For example, if a shell script isintended to be interpreted by the sh shell, the first line should be:

```shell
#!/bin/sh
```

The #! at the beginning of this line, called a “shebang,” is a markerindicating that what follows it is the **path to the interpreter**. (You can examine a script using, say, less or cat to see if it has such a line.)



However, if a script doesn’t include that line, you must tell it explicitly which shell or other interpreter to run it with. You do that by entering theinterpreter’s name with the path to the script as an argument. For example:

```sh
python ~/Documents/my-python-script.py
sh ~/Documents/my-shell-script.sh
php ~/Documents/my-php-script.php
```



## Run a Program in the Background

To run a program in the background, you simply put a space and anampersand (&) after the program name (and any flags or arguments). Forexample, suppose you want to compress a folder containing hundreds oflarge files. 

```shell
zip -r archive.zip apples &
```



top

type top and you get a full-window list of all your running processes, updated dynamically.



Ps("process status")

PID:

TTY(terminal name):





## Stop a Program

Command + Q

**Note**: You can kill only processes you own (that is, ones started under your user account). To kill another user’s processes, you must use sudo (see Perform Actions as the Root User).

- By PID: 
- By name: 

```shell
kill 1232
killall Safari
killall "Microsoft Excel" #(quotation marks added because there's space in the name)
```



## Edit a Text File

nano

```shell
nano file1
```

If file1 is already present, nano opens it; otherwise, it opens a blank file that will be called file1. 

How to do in nano?

- Save: command-s or control-O
- Quit: control-X
- Find: command-F, or control-W



## [Create Shell Script](){#sh}

### Step1. :Start with an Empty Text File

```shell
nano test.sh
```

### Step2: Insert the Shebang

```sh
#!/bin/zsh
```

### Step 3: Add One or More Commands 

```
echo "Hello! The current date and time is:" 
date 
echo "And the current directory is:" 
pwd 
```

The echo command simply puts text on the screen



```sh
chmod u+x test.sh 
./test.sh
```





# Customize Your Defaults

## Startup Files

```
nano ~/.zshrc
```





# Real World

Open 

```
open directory
open -a Safari
```

The open -a command is amazingly smart



# Work with Permissions



# Advanced Topics

在Terminal里使用zsh 犹如在 IDLE里使用python，完全是折磨人。



## Pipe: |

管道函数用于复合函数

最基本的用法是

```shell
ls /Users/nymath
/Users/nymath | ls
```

设想一下，你想在terminal里使用复合函数




```shell
program | other-program
```

## Redirect Output >

Rediect: 重新调配

```shell
ls /Users/nymath > ~/Desktop/prefs.txt  #replace
ls /Users/nymath >> ~/Desktop/prefs.txt  #add
```



## Rediect Input <



## Get a Grip on grep

Grip: 抓牢

Grep: 



## [Add Logic to Shell Scripts](#sh)

Nano: 1e-9

```
nano test.sh
```

```shell
#!/bin/zsh
echo "Hello! The current date and time is:" 
date 
echo "And the current directory is:" 
pwd
city="New York" #there are no spaces around the = sign
echo $city # echo acts as print in R. Also, 
```



### Variable and Input

In zsh and bash, variables are about as simple as they get in any programming language.

注意，调用变量时需要加上$，否则在zsh中，City代表字符串"City"

### Turn a Command-Line Argument into a Variable

When you enter a script name **followed** by a space and one or more terms, each term is automatically assigned to variables called \$1, \$2, \$3, and so on in the order the terms were typed.

```shell
nano test.sh
#!/bin/zsh
echo "The first three arguments you entered were $1, $2, and $3." 
./test.sh Alice Bob Carol 
--------------------------------------------------
The first three arguments you entered were Alice, Bob, and Carol. 
```



### Put the Output of a Command into a Variable

The last variable trick I want to mention is useful when your script needs to run a command and then do something with that command’s output.

To do this, surround the command in question (including any flags or arguments) in parentheses

```shell
today=$(date)
```





### Get Interactive User Input

```shell
nano test.sh
#!/bin/zsh
echo "What do you have to say for yourself?" 
read reply 
echo "Oh yeah? Well, have fun, $reply!" 
```





## Flow Control

Basic Structure:

```shell
if [ condition to test]
then
	action to take
fi
```



### If

```shell
#!/bin/zsh
echo "Pick a number."
read reply
if [ $reply -lt 5 ]; then                 # -le means <=, lt means <	
	echo "$reply is less or equal than 5" 
elif [ $reply -eq 5]l then
else
	echo "$reply is greater than 5"
fi
```



Logit:

- And: &&
- Or: ||
- NOT: !



### While Loops

Basic Structure:

```shell
while [ condition to test ]
do
	stuff to do
done
```



Example

```shell 
#!/bin/zsh
count=1
while [ $count -le 10]
do
	echo "$count"
	((count++))           # count++ is equivalent to count += 1 or count = count+1
done
```



### For Loops

Basic Structure:

```shell
for variable in list
do
	stuff to do
done
```



Example:

```shell
#!/bin/zsh
for i in 1 2 3 4 5
do
	echo "This is iteration number $i"
done

for i in {1..5}
for i in Red Orange Yellow
for i in New\ York San\ Francisco
for i in "New York" "San Francisco"
```



## Math

When it comes to math, bash is at about first-grade level, while zsh is a bit better out of the box and can be extended even further with optional modules. 











-------------------
|firss|sec|
|----|----|
|123|123|





















