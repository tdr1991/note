# 删除镜像

1 查看所有的容器

docker ps -a

2 删除依赖于镜像的容器

docker stop id  \#停止容器

docker stop ${docker ps -a}  \#停止所有容器

docker rm id  \#容器ID号

docker rm ${docker ps -a}  \#删除所有容器

3 删除镜像

docker images id  \#镜像id



