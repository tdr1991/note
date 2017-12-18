# 创建Docker用户组

由于Docker是在root或有sudo权限下安装的，所以每一使用都要切换到root或加sudo。为了避免这种情况，可以创建一个Docker用户组

1 使用有sudo权限的帐号登录系统。

2  创建docker分组，并将相应的用户添加到这个分组里面。

sudo usermod -aG docker your\_username

3 退出，然后重新登录，以便让权限生效。

4 确认你可以直接运行docker命令。

docker run hello-world

