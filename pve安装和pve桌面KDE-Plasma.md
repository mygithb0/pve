


用U盘下载一个pve的镜像
制作U盘安装工具
插入usb接口
重启电脑
进入bios将启动顺序改成U盘启动
注意bios里面的“cpu允许虚拟化”要打开
以华硕主板为例


安装pve
将pve的端口和ip地址设为
192.168.0.200:8006


pve安装以后

pve账号
root
pve密码
123456




用另一台电脑再同一个局域网用final shell连接上这个pve服务器
192.168.0.200
root
123456

# 安装pve桌面版

安装pve的kde桌面的教程
https://www.bilibili.com/video/av892036573/


更新软件源


PVE 虚拟机主机 更换国内源以及解决无效订阅的问题
星空人装备
已于 2023-04-20 20:18:23 修改 489
收藏
分类专栏： PVE 文章标签： debian linux 服务器
版权
PVE 专栏收录该内容
2 篇文章 0 订阅
订阅专栏
1、PVE更换国内源

 注：本文以 pve 7.3.3 为例。

替换前建议先更新下证书，否则可能由于证书不可用导致 https 无法使用，进而无法下载所有软件。

```
apt install apt-transport-https ca-certificates
```


首先替换通用软件源， Debian 的软件源配置文件是 /etc/apt/sources.list，备份后将其中内容修改为以下即可。
```
# 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye main contrib non-free
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye main contrib non-free
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-updates main contrib non-free
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-updates main contrib non-free

deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-backports main contrib non-free
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-backports main contrib non-free

deb https://mirrors.tuna.tsinghua.edu.cn/debian-security bullseye-security main contrib non-free
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian-security bullseye-security main contrib non-free

```

 ctrl+x 再按Y，回车，就可以完成。

之后替换 pve 软件源，pve 镜像默认的 pve 软件源配置文件是 /etc/apt/sources.list.d/pve-enterprise.list ，备份后将其中内容替换为以下即可：(修改步骤同前面。)
```
deb https://mirrors.tuna.tsinghua.edu.cn/proxmox/debian bullseye pve-no-subscription
```


最后更新下，速度很快：

```
apt-get update
```

2
```
apt-get upgrade
```

## 二、一条命令进行安装

默认情况下，KDE Plasma 在 [Debian 11](https://www.yundongfang.com/Yuntag/debian-11) 基础存储库中可用。现在运行以下命令在 Debian 系统上[安装 KDE Plasma](https://www.yundongfang.com/Yuntag/%e5%ae%89%e8%a3%85-kde-plasma) 桌面环境：

```
apt-get install task-kde-desktop
```


硬件重启PVE主机
看启动界面有没有变化了

## 三、设置用户名和密码


创建admin用户
```
useradd -m admin
```
例如

```
useradd -m a
```

设置admin用户密码

```
passwd admin
```

例如
```
passwd a
```
例如
```
123456
```


设好以后pve右上角重启按钮重启
就会出现桌面账号的框了

桌面账号
a
桌面密码
123456

更改语言为中文



# 桌面账号
桌面账号
a
桌面密码
123456




更改语言为中文
system settings》personalization》regional settings》language》add languages》加入简体中文》把简体中文排序调整到上面第一位》apply保存

登出系统再登入
开始菜单》leave》settion》log out》OK

百度搜索中下载和安装firefox的linux版本的浏览器
下载以后会自动安装


# pve操作界面

https://192.168.0.200:8006

# pve账号
pve账号https
root
pve密码
123456