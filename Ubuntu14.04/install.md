# 安装Ubuntu14.04

## 下载Ubuntu14.04镜像

[https://www.ubuntu.com/download](https://www.ubuntu.com/download)

## 制作U盘启动盘

利用UltraISO软件制作启动盘

[https://cn.ultraiso.net/xiazai.html](https://cn.ultraiso.net/xiazai.html)

## 安装Ubuntu

进入BIOS界面设置U盘启动

## 配置网络

如果需要指定IP可以参考以下配置

1.配置好IP、子网掩码、网关和DNS

## ![](/Ubuntu14.04/assets/1_1.png)

![](/Ubuntu14.04/assets/1_2.png).

2.根据路由信息添加相应的路由

sudo route add -net 172.20.0.0/16 gw 210.75.253.2

添加后的路由信息如下

![](/Ubuntu14.04/assets/1_3.png)3.

3.测试

ping www.baidu.com

![](/Ubuntu14.04/assets/1_4.png)

## 安装显卡驱动、cuda

[https://developer.nvidia.com/cuda-downloads](https://developer.nvidia.com/cuda-downloads)

## 安装配置远程桌面服务

参考    [Ubuntu14.04/win10conubuntu16.04.md](/Ubuntu14.04/win10conubuntu16.04.md)

