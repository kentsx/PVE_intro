---
description: 基于PVE设备不作为主路由使用
---

# 安装PVE

{% hint style="warning" %}
如果PVE设备要做主路由的，请看一下司波图的讲解，包括后面关于eth0,enp1s0等等找对应网口的部分。
{% endhint %}

## 下载PVE

建议下载官方原版吧，这样最放心不是，嫌弃速度慢的，IDM等等自己想办法吧

下载地址：[https://www.proxmox.com/en/downloads/category/iso-images-pve](https://www.proxmox.com/en/downloads/category/iso-images-pve)

## 制作镜像（U盘）

官方教程（需要中学英语水平）：[https://pve.proxmox.com/wiki/Prepare\_Installation\_Media](https://pve.proxmox.com/wiki/Prepare\_Installation\_Media)

我大致写一下：

* 官方提及了Etcher、Rufus两个写盘软件，但明确不要用UNetbootin。
* 我用的Rufus，非常轻量级，整个软件大概1-2MB吧，下载地址：[https://rufus.ie/](https://rufus.ie/zh/)这个有中文网站）
* 用Rufus注意：选择写入模式时，一定要<mark style="color:red;">选择DD模式</mark>！

## 安装前的准备

* 有多个网口的情况下，确定好设备的管理网口，该网口已经连接上主路由，主路由已经联网。这里以主路由ip为 192.168.10.1

## 安装PVE

1. 插入U盘以后开机，设置BIOS的启动项为U盘，系统会自动引导进入PVE的安装程序。
2. 前面几步包括选安装盘、设置国家时区都比较简单  时区`Asia/Shanghai`
3. 设置网络界面，最好选择静态IP，比如输入192.168.10.200/24  `/24为掩码`&#x20;
4. 等待安装完毕后，设备自动重启，这是可以拔出U盘了
5. 设备依然保持联网情况下，另一台局域网内电脑就可以通过`https://192.168.10.200:8096`进行登录web-ui了

## 操作台显示温度信息

引用了[https://github.com/ivanhao/pvetools](https://github.com/ivanhao/pvetools)

我的建议：虽然原始的企业源没啥用，但还是留着个备份，当然和ivanhao说的直接`rm`也是OK，看个人喜好。

```
# 备份做法
mv /etc/apt/sources.list.d/pve-enterprise.list /etc/apt/sources.list.d/pve-enterprise.listbk
```

接着输入以下命令就可以了，会启动一个视窗界面，光标上下选择，回车确认。

```
export LC_ALL=en_US.UTF-8
apt update && apt -y install git && git clone https://github.com/ivanhao/pvetools.git
cd pvetools
./pvetools.sh
```

我自己并没有能成功去掉订阅，也不知道是不是我备份了企业源，但这个也无伤大雅。
