---
description: 用portainer安装
---

# Docker之Transmission

前面的一些操作见 [docker-zhi-jellyfin.md](docker-zhi-jellyfin.md "mention")

linuxserver关于transmission的介绍： [https://hub.docker.com/r/linuxserver/transmission](https://hub.docker.com/r/linuxserver/transmission)

## 具体配置

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption><p>镜像及端口配置</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption><p>volume配置</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>environment配置</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>environment  权限配置</p></figcaption></figure>

{% hint style="warning" %}
一定要配PUID和PGID权限，我设了0，相当于root用户，不然会有问题

* 可以尝试官方文档中的1000
{% endhint %}

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption><p>自动重启</p></figcaption></figure>

由于我们没有挂载默认的incomplete文件夹，如果不设置，会出现文件先下载到incomplete中，再转到movie等文件夹中的情况；可以在transmission中设置，把临时目录不勾选。

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

