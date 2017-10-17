# 文件/文件夹相关操作

## 本地与远程主机互传文件/文件夹

1.使用sftp

2.使用scp

3.使用ftp，请参考 ftp 搭建那章  [Ubuntu14.04/ftp.md](/Ubuntu14.04/ftp.md)

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

![](/Ubuntu14.04/assets/7_3.png)

2.sftp

 ![](/Ubuntu14.04/assets/7_5.png)

sftp user@IP   \# 连上远程主机

命令跟 ftp 模式差不多，指的是操作远程主机，如果操作本地主机，在命令前加 字符 l 就行

![](/Ubuntu14.04/assets/7_4.png)

