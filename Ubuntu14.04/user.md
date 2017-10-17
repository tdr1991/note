# 用户管理

## 创建用户

使用命令adduser才会自动创建家目录，useradd并不会，只是在/etc/passwd文件添加信息

adduser tdr

或者  useradd -m tdr  \# -m表示创建家目录

![](/Ubuntu14.04/assets/7_1.png)

Linux用户权限

在Linux操作系统中，root的权限是最高的，相当于windows的administrator，拥有最高权限，能执行任何命令和操作，在Linux系统中，通过UID来区分用户的权限级别，UID等于0，表示此用户具有最高权限，也就是管理员，其他的用户UID依次增加，通过/etc/passwd用户密码文件可以查看每个用户的独立UID

Linux文件或目录的用户、组、其他人权限

Linux中每一个文件或者目录都包含一个用户权限、一个组的权限、其他人权限

如下所示：

标红第一个root表示该文件所有者是root用户，第二个root代表该文件的所属组为root组，其他用户这里默认不标出。

\#ls -l test.txt&lt;/div&gt;

-rw-r--r-- 1 root root 91 may 7 20:21 test.txt

第一位表示文件类型，-表示文件，d表示目录；后面每三位为一组。

第一组:2-4位表示文件所有者的权限，即用户user权限，简称u 在这里表示root用户有\(rw-\)的权限，可读\(r\)与可写\(w\)的权限，没有可执行\(x\)权限

第二组:5-7位表示文件所有者所属组成员的权限，group权限，简称g 这里表示root组成员有\(r--\)的权限，只有可读的权限。

第三组:8-10位表示所有者所属组之外的用户权限，other权限，简称o 这里表示其他人有\(r--\)的权限，只有可读的权限。

修改文件或文件夹的权限

\[root@localhost /\]chmod u+r test.txt //表示为root用户添加读的权限

\[root@localhost /\]chmod g-w test.txt //表示为root组去除写的权限

\[root@localhost /\]chmod o+x test.txt //表示其他人添加可执行的权限

如果我们要为所有用户添加所有rwx权限

\[root@localhost /\]chmod u=rwx,g=rwx,o=rwx test.txt

为了能更简单快捷的使用和熟悉权限，rwx权限可以用数字来表示，分别表示为r\(4\)、w\(2\)、x\(1\)

\[root@localhost /\]chmod 456 test.txt //表示root用户对test具有r\(4\)的权限，root组队test文件具有r\(4\)+x\(1\)的权限，其他人具有rw的权限

\[root@localhost /\]chmod 000 test.txt //表示去除所有权限

## 赋予用户sudo权限

修改  /etc/sudoers 文件，文件只有只读权限，添加写权限

chmod u+w /etc/sudoers

编辑 /etc/sudoers 文件，找到下面这行

root    ALL=\(ALL:ALL\) ALL

将 root 换成 需要赋予sudo权限的用户名

vim /etc/sudoers

username ALL=\(ALL:ALL\) ALL

如果需要设置成不需要密码，则在最后一个 ALL 前面添加  NOPASSWD: 

username ALL=\(ALL:ALL\) NOPASSWD: ALL

恢复文件 /etc/sudoers 权限设置

chmod u-w /etc/sudoers

![](/Ubuntu14.04/assets/7_2.png)







