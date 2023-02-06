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

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>端口配置</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>volume配置，注意bind模式</p></figcaption></figure>

{% hint style="danger" %}
这里不能配置/config目录，一旦配置，会无法启动jellyfin

原因分析如下：

因为docker的绑定机制是先缓存在docker中，在文件不被写入后再存入绑定目录。但由于我们做了2次映射（docker-->LXC-->NAS），这里就会出现一个时间差，即缓存到NAS的时候，LXC对NAS的文件读写还在进行，而docker又要进行下一次的jellyfin.db读写，出现锁死问题。

虽然官方文件说/config会很大，但我可能局限于局域网播放，暂时没有出现这个文件很大的问题；因为比较大的文件应该是出现在转码时候产生的。

* Jellyfin设置时见媒体图像保存到媒体所在文件夹！！
* 后续我再看如何解决！！
{% endhint %}

{% hint style="success" %}
前面问题的基本和我分析的差不多，主要出现在`byte range locks`
{% endhint %}

{% hint style="success" %}
在安装calibre-web时同样也出现了这个问题，解决方案参考此文：

[https://coderwall.com/p/zrxobw/calibre-libraries-on-nas](https://coderwall.com/p/zrxobw/calibre-libraries-on-nas)

在mount的时候加入nobrl参数。

针对Jellyfin，只有在/config目录下有db文件，有些docker应用会多处，可根据实际需求设置nobrl。

//192.168.10.201/appdata/J4125 /mnt/appdata cifs nobrl,credentials=/root/.smbcredentials,iocharset=utf8 0 0
{% endhint %}

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

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
