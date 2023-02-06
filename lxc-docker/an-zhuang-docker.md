# 安装Docker

## 安装Docker

```
apt install curl -y
curl -sSL https://get.daocloud.io/docker | sh
```

<figure><img src="../.gitbook/assets/image (5) (2).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
出现这个界面，表示Docker已经安装好了
{% endhint %}

## 安装Portainer

{% hint style="info" %}
为后续方便界面化操作Docker，安装portainer
{% endhint %}

```
docker volume create portainer_data
docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce
```

## 进入Portainer界面

Portainer的web界面为LXC虚拟机IP:9000

在LXC安装中，设置的是LXC的IP为192.168.10.198，所以Portainer为192.168.10.198:9000

首次登录会要输入账号密码，自行定义，是以后进入Portainer使用的。

