---
description: Docker安装
---

# Docker之HomeAssistant

```
docker run -d \
  --name homeassistant \
  --privileged \
  --restart=unless-stopped \
  -e TZ=Asia/Shanghai \
  -v /PATH_TO_YOUR_CONFIG:/config \
  --network=host \
  ghcr.nju.edu.cn/home-assistant/home-assistant:stable
  # 南京大学的镜像
```
