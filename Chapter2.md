<!-- Chapter2.md-- >

# 第二章 学习Linux

## 2.1 从图形界面说起

&emsp;&emsp;在Windows下，我们习惯于使用各种具有完善图形界面的软件，毫无疑 问，图形界面大大降低了普通人使用电脑的成本，甚至个人计算机的普 及，图形界面都功不可没，在Linux下也有图形界面（俗话说的桌面）， 通过以下文字，我们可以对其有初步的了解：
>相对于现在的 Windows 系统，UNIX/Linux 本身是没有图形界面 的，我们通常在 UNIX/Linux 发行版上看到的图形界面实际都只是 运行在 Linux 系统之上的一套软件,而 Linux 上的这套软件以前是 XFree86，现在则是 xorg（X.Org），而这套软件又是通过 X 窗口 系统（X Window System，也常被称为 X11或X）实现的，X本身 只是工具包及架构协议，而 xorg 便是 X 架构规范的一个实现体， 也就是说它是实现了 X 协议规范的一个提供图形界面服务的服务 器，就像实现了 http 协议提供 web 服务的 Apache 。如果只有服 务器也是不能实现一个完整的桌面环境的，当然还需要一个客户 端，我们称为 X Client，像如下几个大家熟知也最流行的实现了客 户端功能的桌面环境 KDE，GNOME，XFCE，LXDE 。&emsp;&emsp; 注：以上 文字引自《Linux基础入门》

&emsp;&emsp;当然也许你早就知道Linux的正确打开方式是使用命令行（呃..啥是命令 行？），不过看了对Linux图形界面的描述后，是不是更加理解为啥我们 要用命令行了。那接下来就说说啥是命令行?

## 2.2 命令行、终端，shell和console

&emsp;&emsp;（想不到吧.jpg）是不是突然冒出的四个名词让你顿时懵逼？别着急，我们一个一个来解释。

### 2.2.1 命令行(CLI)

&emsp;&emsp;你们记不记得你们在玩minecraft的时候时常用到的一种操作，就是在输入框内输入一些指令，然后进行一些神奇操作？这就是一种类似于命令行的东西啦。
>命令行界面是相对于图形界面而言的，较图形用户界面节约计算 机系统的资源。在熟记命令的前提下，使用命令行界面往往要较 使用图形用户界面的操作速度要快。命令行中，可以使用脚本语 言和宏语言，以其提供更加丰富的控制与自动化的系统管理能 力。&emsp;&emsp;注：以上文字引自维基百科。

&emsp;&emsp;看了上面的文字后，你是否对命令行有了更加全面的了解呢。其实这些看起来很高端的名词，实际上都是一些易于理解的东西啦。

### 2.2.2 终端(Terminal)

&emsp;&emsp;终端特指计算机或通信网络中输入或输出信息的装置，通常由键盘和显 示器等组成。但是使用Mac或者安装好了Ubuntu的童鞋会发现有一个程 序也叫终端（Terminal），在某种意义上，终端还是我们与系统交互的窗 口，严格来讲，我们现在在系统中运行的终端程序只是终端模拟器。常 见的终端模拟器有以下几个：

* gnome-terminal，
* kconsole，
* xterm，
* rxvt，
* kvt，
* nxterm
* eterm

&emsp;&emsp;这里还得插一句：终端本质上是对应着 Linux 上的 /dev/tty 设备（试着联系前文），Linux 的多用户登陆就是通过不同的 /dev/tty 设备完成的.

### 2.2.3 shell(壳)

&emsp;&emsp;有壳就有核，核指的 是 UNIX/Linux 内核，Shell之所以叫Shell 是因为它隐藏了操作系统底层的 细节。我们可以换个大家一下就能懂的词来理解Shell:命令解析器（手动滑稽）。

&emsp;&emsp;比如说当我们在终端中输入node，按回车，会启用node解释器，输入 python按回车会启动Python解释器，之后就可以在里面输入并执行对应语言的代码啦。于是这里的node和python也是一种shell。

在UNIX/Linux中常见的shell有：

* bash（GNU/linux的默认shell）
* zsh
* ksh
* csh And so on......

等等，Ubuntu 终端默认使用的是 bash。本文后面对shell命令的讲解也 大多基于bash。

### 2.2.4 console

&emsp;&emsp;从字面上来讲，console是控制台的意思，现在的console一般与终端在外表上没什么区别，不过其在功能上却大不相同，console的出现有其历史原因，简单的说来，就是在以前电脑还是很稀缺的物件的年代，一台电脑是会陪伴多套终端的，这时候就需要专门的系统管理员利用console来管理系统。目前对一般人来说console的作用可能没有那么大了，不过可能其还是会在一些特殊场景下有很大的作用，比如说javascript的console 可以用来输出啊debug啊之类的。

终端分字符终端和图形终端：

* 字符终端(CharacterTerminal)也叫文本终端(TextTerminal)，是只能接收和输出文本信息的终端。
* 图形终端(Graphics Terminal)不但可以接收和输出文本信息，也可以输出图形图像。

一般说来字符终端的的标准是DEC公司1978制造的型号为VT100的终端。而图形终端的标准是X Window，它是大多数Unix-like系统GUI界面的基础，xterm是Unix世界里最著名的图形终端模拟程序（虽然长得贼丑 emmm）。

以Ubuntu具体说来，它默认提供七个终端，其中第一个到第六个虚拟控制台是全屏的字符终端，第七个虚拟控制台是图形终端，用来运行GUI程序，按快捷键CTRL+ALT+F1，或CTRL+ALT+F2…….CTRL+ALT+F6，CTRL+ALT+F7可完成对应的切换,安装了虚拟机的童鞋可以动手尝试一下哈。

## 2.3 开始使用shell

&emsp;&emsp;shell可能是我们在Linux下使用最多的工具了，本小节我们我们以bash为例，当然zsh下以下命令也是适用的，我们先熟悉一下shell的基本操作。

### 对输入输出的描述

命令行的操作分为输入和输出两个方面：

* 输入：打开终端，按键盘输入，按回车结束输入并执行（是不是很简单啊）；
* 输出：输出会返回你想要的结果，比如你看的是文件，就会返回文件的内容。如果是执行的程序，执行失败会告诉你哪里错了，如果施行成功会没有输出，这是linux的哲学：没有结果就是最好的结果。

### 提高shell的输入效率

合理的使用快捷键确实可以明显的提高工作效率，对shell常用快捷键的 总结如下：
Tap:点击Tab键可以实现命令补全,目录补全、命令参数补全;

* Ctrl+c:强行终止当前程序（常用）;
* Ctrl+d:键盘输入结束或退出终端（常用）;
* Ctrl+s:暂停当前程序，暂停后按下任意键恢复运行;
* Ctrl+z:将当前程序放到后台运行，恢复到前台为命令fg;
* Ctrl+a:将光标移至输入行头，相当于Home键;
* Ctrl+e:将光标移至输入行末，相当于End键;
* Ctrl+k:删除从光标所在位置到行末,常配合ctrl+a使用;
* Alt+Backspace:向前删除一个单词，常配合ctrl+e使用;
* Shift+PgUp:将终端显示向上滚动;
* Shift+PgDn:将终端显示向下滚动; 上下方向键:浏览历史输入记录（很容易坏掉的方向键emmm）;

熟练运用上述的操作技巧将大大提升我们命令行的操作效率，不过真正 解决问题需要应用各种bash命令，下面对常用命令进行简单的介绍：

### 常见的bash命令

1. ls:列出某文件夹下的文件，加参数可实现更细致的功能，比如

```
ls -a #列出所有文件，包括隐藏文件
ls -l #列出文件及其详细信息
```

2. cd: 切换目录,cd到不存在的目录时会报错
3. pwd: 打印当前目录的绝对路径
4. cat: 读取某一个文件内的内容
5. wc：获取某一个文件的行数和字数，举栗：

```
    $ wc package.json
    # 79     175     2712package.json
```
6. cp:复制东东
   
   cp -r: 递归复制（比如文件夹）
7. mkdir:创建目录
8. rmdir：删除目录
9. rm: 删除东东

    rm -rf:r删除内部所有文件，f参数表示强制(force)
10. mv：移动,举栗：

```
mv photos.jpg Photos #将photos移动到文件夹Photos下
```

11. sort：排序
12. diff：比较两个文件的异同

And so on......

### 系统相关

1. date:获取当前时间
2. uname:返回系统名称
3. hostname：返回系统的主机名称

And so on .........

### 网络相关

1. host [xx.xxx.com]：显示某域名相关托管服务器/邮件服务器
2. ping [hostaddress]: 检测连接

And so on.........

### 通配符（Globbing）：

使用命令时可在参数中使用通配符

* *：匹配 0 或多个字符，如ls \*.html将匹配所有以html结尾的文 件,ls b\*.png将匹配所有以b开头，png结尾的文件；
* ?：匹配任意一个字符,如ls abc?.png 可匹配abcd.png/abce.png
* [list]:匹配 list 中的任意单一字符 
* [!list]:匹配 除list 中的任意单一字符以外的字符 
* [c1-c2]:匹配 c1-c2 中的任意单一字符 如：[0-9] [a-z] 
* {string1,string2,...}:匹配 string1 或 string2 (或更多)其一字符串，如 {css,html}， ls app.{html.css}将匹配app.css 和app.html; 
* {c1..c2}:匹配 c1-c2 中全部字符 如{1..10} 注意通配符大小写敏感 emmm

上文只对常见命令进行了简单的描述（进行了吹水操作），其中一些命令在下文讲到具体应用场景时还会详细的说明。结合刚刚所说的这些命令，我们来理解Linux是一个怎么样的系统。
