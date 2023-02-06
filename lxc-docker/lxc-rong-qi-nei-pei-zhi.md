# LXC容器内配置

{% hint style="warning" %}
LXC容器内
{% endhint %}

## 换Debian源

```
mv /etc/apt/sources.list /etc/apt/sources.list.bk
nano /etc/apt/sources.list
```

### 粘贴

```
deb https://mirrors.ustc.edu.cn/debian/ bullseye main non-free contrib
deb-src https://mirrors.ustc.edu.cn/debian/ bullseye main non-free contrib
deb https://mirrors.ustc.edu.cn/debian-security/ bullseye-security main
deb-src https://mirrors.ustc.edu.cn/debian-security/ bullseye-security main
deb https://mirrors.ustc.edu.cn/debian/ bullseye-updates main non-free contrib
deb-src https://mirrors.ustc.edu.cn/debian/ bullseye-updates main non-free contrib
deb https://mirrors.ustc.edu.cn/debian/ bullseye-backports main non-free contrib
deb-src https://mirrors.ustc.edu.cn/debian/ bullseye-backports main non-free contrib
```

### 更新

```
apt update
apt upgrade -y
```
