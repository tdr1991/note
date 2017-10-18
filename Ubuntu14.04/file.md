# 文件/文件夹相关操作

## 本地与远程主机互传文件/文件夹

1.使用sftp

2.使用scp

3.使用ftp，请参考 ftp 搭建那章  [Ubuntu14.04/ftp.md](/Ubuntu14.04/ftp.md)

4.支持断点传输 rsync

### win10与Ubuntu16.04之间相互传文件/文件夹

1.使用scp，下载pscp软件（windows系统没用安装这样的软件，需要借助第三方的）

[https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

![](/Ubuntu14.04/assets/6_1.png)

如果想在任何路径下都能使用pscp则将其放置在windows的system32目录下否则调用pscp时使用绝对路劲

从Ubuntu14.04下载文件/文件夹到本地

/d/pscp.exe -r tdr@210.75.253.131:/data/tdr/test /e/

从本地上传文件/文件夹到Ubuntu14.04

/d/pscp.exe -r /e/tdr/HMP/HM16STR/suminfo/\* tdr@210.75.253.131:/data/tdr/HMP/HM16STR

2.使用sftp，下载psftp

[https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html](https://www.gitbook.com/book/tdr1991/note/edit#)

![](/Ubuntu14.04/assets/6_2.png)

3.使用 git，才发现 git 太强大了

在 git 中，它可以把 windows 当作 linux 文件系统，所以可以使用 scp，sftp 命令，与下一节使用完全一样。

### linux与Ubuntu16.04之间相互传文件/文件夹

1.scp

如果完全清楚远程的目录，则可以直接使用该方式

![](/Ubuntu14.04/assets/6_3.png)

2.sftp

![](/Ubuntu14.04/assets/6_4.png)

sftp user@IP   \# 连上远程主机

命令跟 ftp 模式差不多，指的是操作远程主机，如果操作本地主机，在命令前加 字符 l 就行

![](/Ubuntu14.04/assets/6_5.png)

3.rsync

rsync -P --rsh=ssh localfile user@1.2.3.4:remotedir

如果觉得 rsync -P --rsh=ssh 太麻烦，可以用 alias 命令起个别名

alias scpr="rsync -P --rsh=ssh"

## 系统任务相关

bg、fg、jobs、&、ctrl+z、nohup、ps、kill

执行上面的文件传输任务时，通常需要传输的文件很大，如果担心ssh中途中断，ctrl+z 将任务暂停，放入后台，注意红色数字

![](/Ubuntu14.04/assets/6_7.png)

运行暂停任务， bg 5

![](/Ubuntu14.04/assets/6_8.png)

查看后台任务， jobs 只能查看当前终端的后台任务，而 ps 可以查看所有终端的

![](/Ubuntu14.04/assets/6_9.png)

如果需要将任务放到前台运行，执行  fg 5

如果输入命令时希望后台运行，则在命令后面直接加  &  就可实现后台运行

在命令前 加 nohup  表示不挂断运行

kill命令：结束进程

（1）通过jobs命令查看jobnum，然后执行   kill %jobnum

（2）通过ps命令查看进程号PID，然后执行  kill %PID。kill -9 %PID    \#强行结束进程

如果是前台进程的话，直接执行 Ctrl+c 就可以终止了

## 文件压缩与解压缩

### 压缩

compress、gzip、bzip2

gzip 是为了取代 compress 并提供更好的压缩比而成立的，那么 bzip2 则是为了取代 gzip 并提供更佳的压缩比而来的

gzip与bzip2的用法几乎相同

![](/Ubuntu14.04/assets/6_6.png)

gzip file file.gz

注意用此命令压缩源文件会删除，变成以 .gz 为后缀的文件，如需恢复，执行解压缩

### 解压缩

gzip -d file.gz

如果需要解压缩整个文件夹下的文件，可以使用以下脚本

find ./dir -name “\*.gz” -exec gzip -d {} \;

### 打包

![](/Ubuntu14.04/assets/6_10.png)

压　缩：tar -jcv -f filename.tar.bz2 要被压缩的文件或目录名称

查　询：tar -jtv -f filename.tar.bz2

解压缩：tar -jxv -f filename.tar.bz2 -C 欲解压缩的目录

那个 filename.tar.bz2 是我们自己取的档名，tar 并不会主动的产生创建的档名喔！我们要自订啦！ 所以扩展名就显的很重要了！如果不加 \[-j\|-z\] 的话，档名最好取为 \*.tar 即可。如果是 -j 选项，代表有 bzip2 的支持，因此档名最好就取为 \*.tar.bz2 ，因为 bzip2 会产生 .bz2 的扩展名之故！ 至於如果是加上了 -z 的 gzip 的支持，那档名最好取为 \*.tar.gz 喔！了解乎？

另外，由於『 -f filename 』是紧接在一起的，过去很多文章常会写成『-jcvf filename』，这样是对的， 但由於选项的顺序理论上是可以变换的，所以很多读者会误认为『-jvfc filename』也可以～事实上这样会导致产生的档名变成 c ！ 因为 -fc 嘛！所以罗，建议您在学习 tar 时，将『 -f filename 』与其他选项独立出来，会比较不容易发生问题。

