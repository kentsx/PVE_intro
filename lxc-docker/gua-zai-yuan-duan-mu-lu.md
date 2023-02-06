---
description: 安装SMB组件并创建共享目录
---

# 挂载远端目录

{% hint style="warning" %}
LXC容器内
{% endhint %}

## 安装SMB插件

```
apt install cifs-utils -y
```

## 创建SMB连接的密码文件

{% hint style="info" %}
注意保护文件，此处为明文密码

密码文件位置在/root/.smbcredentials
{% endhint %}

```
nano ~/.smbcredentials
```

1、设置SMB登录密码，自行替换：

```
username=smb_share
password=share_password
```

2、在LXC容器中创建挂载点

```
mkdir /mnt/file/path
```

3、、修改自动挂载文件

```
nano /etc/fstab
```

{% hint style="info" %}
如我要挂载一个电影文件夹

mkdir /mnt/movie
{% endhint %}

4、加入挂载位置，自行替换

```
//$smb_server/share /mnt/nas_share cifs credentials=/root/.smbcredentials,iocharset=utf8 0 0
//**远端IP***/路径   ***挂载点路径*** **** ******密码文件位置***************** 注意相互之间空格
```

{% hint style="info" %}
我的远端文件在192.168.10.201的NAS中，远端文件也有一个/movie文件夹

//192.168.10.201/movie /mnt/movie cifs credentials=/root/.smbcredentials,iocharset=utf8 0 0
{% endhint %}

5、重启LXC容器

```
reboot
```

{% hint style="info" %}
此时进入相应目录，ls -la就已经能够看到远端的文件和文件夹了
{% endhint %}
