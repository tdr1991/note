# 安装jupyter notebook

安装参照 [Ubuntu14.04/jupyter.md](/Ubuntu14.04/jupyter.md "安装")

注意：在浏览器打开时，如遇到

\[W 10:16:14.157 NotebookApp\] SSL Error on 8 \('192.168.0.109', 51582\): \[SSL: WRONG\_VERSION\_NUMBER\] wrong version number \(\_ssl.c:590\)

这样的错误提示，则要在浏览器的地址栏前面加入  https://

解决办法参考的是  [http://blog.csdn.net/u014265088/article/details/53116974](http://blog.csdn.net/u014265088/article/details/53116974 "ssl error")

启动时记得做好端口映射

nvidia-docker run -p 8888:8888 -it -v /data:/data tdr jupyter notebook --allow-root

