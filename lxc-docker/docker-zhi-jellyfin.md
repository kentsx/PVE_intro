---
description: 用portainer安装
---

# Docker之Jellyfin

## 进入local的Container

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

## 添加容器

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
我的设备为J4125，建议使用 <mark style="color:blue;">`nyanmisaka/jellyfin`</mark>

具体设置可以参考这linuxserver里的要求，N大没有具体写

<mark style="color:blue;">``</mark>[<mark style="color:blue;">`https://hub.docker.com/r/linuxserver/jellyfin`</mark>](https://hub.docker.com/r/linuxserver/jellyfin)<mark style="color:blue;">``</mark>
{% endhint %}

{% hint style="info" %}
里面涉及的一些目录，需要在远端NAS等设备上提前建好
{% endhint %}

我的配置如图：

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>端口配置</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption><p>volume部分，注意模式为bind</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption><p>environment部分，非必须</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption><p>自动重启</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption><p>硬件直通，映射给container</p></figcaption></figure>

全部设置完以后，点击 <mark style="color:blue;">`Deploy the container`</mark>

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

等待部署完成，Portainer会跳转回Container list界面，Jellyfin显示已经开始运行后，就可以在`IP:8096`中打开了

## 打开硬件直通

在选择完媒体库信息后，进入Jellyfin的控制台-->播放中

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p>开启硬件解码</p></figcaption></figure>

* [x] 启用VPP色调映射
* [x] 启用色调映射
* [x] 启用备用字体
