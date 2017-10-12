# 文件/文件夹相关操作

## win10与Ubuntu14.04之间相互传文件/文件夹

### win10传文件/文件夹

下载pscp软件

[https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

![](/Ubuntu14.04/assets/6_1.png)

如果想在任何路径下都能使用pscp则将其放置在windows的system32目录下否则调用pscp时使用绝对路劲

从Ubuntu14.04下载文件/文件夹到本地

/d/pscp.exe -r tdr@210.75.253.131:/data/tdr/test /e/

从本地上传文件/文件夹到Ubuntu14.04

/d/pscp.exe -r /e/tdr/HMP/HM16STR/suminfo/\* tdr@210.75.253.131:/data/tdr/HMP/HM16STR

