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

bg、fg、jobs、&、ctrl+z

执行上面的文件传输任务时，通常需要传输的文件很大，如果担心ssh中途中断，ctrl+z 将任务暂停，放入后台，注意红色数字

![](/Ubuntu14.04/assets/6_7.png)

运行暂停任务， bg 5

![](/Ubuntu14.04/assets/6_8.png)

查看后台任务， jobs 

![](/Ubuntu14.04/assets/6_9.png)

如果需要将任务放到前台运行，执行  fg 5

如果输入命令时希望后台运行，则在命令后面直接加  &  就可实现后台运行

## 文件压缩与解压缩

### 压缩

![](/Ubuntu14.04/assets/6_6.png)

gzip file file.gz

注意用此命令压缩源文件会删除，变成以 .gz 为后缀的文件，如需恢复，执行解压缩

### 解压缩

gzip -d file.gz

如果需要解压缩整个文件夹下的文件，可以使用以下脚本

find ./dir -name “\*.gz” -exec gzip -d {} \;

