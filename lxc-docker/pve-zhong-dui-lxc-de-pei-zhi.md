---
description: 配置PVE中的conf参数等
---

# PVE中对LXC的配置

{% hint style="info" %}
在宿主机PVE Shell中执行
{% endhint %}

## 为容器加入渲染器硬件，并关闭AppArmor

```
nano /etc/pve/lxc/[CT_ID].conf
```

{% hint style="success" %}
部分显卡可能需要更新内核才能找到渲染器

如前文所示，此处为<mark style="color:orange;">nano /etc/pve/lxc/100.conf</mark>
{% endhint %}

{% hint style="warning" %}
加入硬件参数：（可先用ls -l /dev/dri查询）

以下参数适用于大部分的Intel核显

最后一句lxc.cap.drop = 参考了该页面

[https://gist.github.com/kuanghan/9aa5dfea243ed109c0878267e2d80b13](https://gist.github.com/kuanghan/9aa5dfea243ed109c0878267e2d80b13)
{% endhint %}

```
lxc.cgroup2.devices.allow: c 226:0 rwm
lxc.cgroup2.devices.allow: c 226:128 rwm
lxc.cgroup2.devices.allow: c 29:0 rwm
lxc.mount.entry: /dev/dri dev/dri none bind,optional,create=dir
lxc.mount.entry: /dev/fb0 dev/fb0 none bind,optional,create=file
lxc.apparmor.profile: unconfined
lxc.cap.drop =
```

