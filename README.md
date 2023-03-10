# 前言

## 面向的使用者

这个教程面向的使用者是和我一样，在摸索PVE、软路由过程中一步一步成长起来的人。我记录下自己走过的坑，遇到的问题以及解决方法，力求为自己之后重装留下回忆，也能帮助那些还在摸索中的人少走写弯路。

## 致谢

在这个教程的记录中，很大程度上都依赖了B站司波图的指导，非常感谢他的无私奉献。

{% embed url="https://www.bilibili.com/video/BV1GY41177Es/?spm_id_from=333.788&vd_source=2c24b7fa14f5faf77c46cbf25e20e036" %}
司波图教程
{% endembed %}

在文中大量引用了他的教案以及代码，所以这里一定要提及他。

他的教程文字版：[https://gitee.com/spoto/PVE\_Generic\_AIO](https://gitee.com/spoto/PVE\_Generic\_AIO)

## 感想

* 我并不非常建议AIO，为何？
  1. 因为之所以会有这篇教程，是因为至今我都不明白的原因，导致了家中的软路由只要一断电重启，在完成的前大概30s，是可以正常联网的；然后因为它里面的软路由需要分配IP给各个家中设备，导致全局瘫痪。我自己的猜想可能与无良ISP搞了云宽带有些关系，导致第一层的IP出现了问题。
  2. 也因此，我重新安装了整个PVE以及里面的LXC、Docker
  3. 当然也“因祸得福”，帮助我粗浅地进一步理解了Docker、Linux下挂载，修复了Jellyfin的自动更新媒体库、转移Transmission到J4125设备上等一些功能
* 我的一些小建议：
  1. 主路由，我这里指的是分配IP给家中那台路由器，无论硬路由还是软路由乃至桥接的，都不要装到AIO中，因为一旦这部分出现bug，家中上网，甚至是想搜索解决方案都会很费劲。路由器，稳字当头，而且一机一用最为稳妥，一旦出现bug，要么刷机重装、要么换设备，都不会影响到家里的其他功能。
  2. 所有的操作都有可能有风险，想清楚了再行动。
  3. 最后，尽最大可能不要使用盗版，支持正版，是对开发者最好的支持。
