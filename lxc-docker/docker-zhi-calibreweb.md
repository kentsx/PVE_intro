---
description: docker命令行安装
---

# Docker之Calibre-web

{% hint style="success" %}
用的`johngong/calibre-web`

``[`https://hub.docker.com/r/johngong/calibre-web`](https://hub.docker.com/r/johngong/calibre-web)``
{% endhint %}

{% hint style="warning" %}
注意：Calibre-web的 volume挂载时都要加nobrl（针对NAS的远端挂载）

[https://coderwall.com/p/zrxobw/calibre-libraries-on-nas](https://coderwall.com/p/zrxobw/calibre-libraries-on-nas)
{% endhint %}

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

```
 docker create  \
    --name=calibre-web  \
    -p 8083:8083  \
    -p 8080:8080  \
    -v /配置文件位置:/config  \
    -v /书库:/library  \
    -v /自动添加文件夹:/autoaddbooks  \
    -e UID=0  \   #这里与作者文档不同
    -e GID=0  \   #这里与作者文档不同
    -e CALIBRE_SERVER_USER=用户名  \
    -e CALIBRE_SERVER_PASSWORD=用户密码 \
    --restart unless-stopped  \
    johngong/calibre-web:latest
```

| 参数           | 说明                                              |
| ------------ | ----------------------------------------------- |
| `本地端口1:8083` | calibre-web web访问端口,默认用户名: admin 默认密码: admin123 |
| `本地端口2:8080` | calibre-server web访问端口                          |
