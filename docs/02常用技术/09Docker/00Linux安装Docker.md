#  [Linux服务器安装Docker](https://www.cnblogs.com/melodyjerry/p/13260398.html)

前阵子在阿里云618活动花“巨款”买下了一个T5型的云服务器，镜像版本为CentOS 7.4。现打算安装Docker。

# 官方文档

https://docs.docker.com/install/linux/docker-ce/centos/

# 卸载旧版

按官方的文档，新版Docker无法覆盖旧版的，所以无比先卸载原来的旧版本

在Linux虚拟机上，我是装有旧版的，但由于服务器是全新的，无任何配置的，可以跳过这步骤

```
# 移除旧版本的 Docker
yum remove docker \
  docker-client \
  docker-client-latest \
  docker-common \
  docker-latest \
  docker-latest-logrotate \
  docker-logrotate \
  docker-selinux \
  docker-engine-selinux \
  docker-engine
```

# 安装 Docker

1. 安装软件包

```
# 安装 Docker 依赖
yum install -y yum-utils device-mapper-persistent-data lvm2
```

1. 配置阿里云Docker Yum源(个人觉的好)

```
# 添加源
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

# 更新 yum 缓存
yum makecache fast
```

1. 安装最新版本的Docker

```
# 安装 Docker-CE
yum install -y docker-ce
 
# 开启 Docker
systemctl start docker
 
# 安装 Docker Compose
curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

# 相关防火墙配置

```
# Docker 和 Swarm 相关防火墙配置
systemctl status firewalld
systemctl start firewalld
firewall-cmd --add-port=9010/tcp --permanent
firewall-cmd --add-port=9020/tcp --permanentfirewall-cmd --add-port=443/tcp --permanent
firewall-cmd --add-port=80/tcp --permanent
firewall-cmd --add-port=80/udp --permanentfirewall-cmd --add-port=22/tcp --permanent
firewall-cmd --add-port=22/udp --permanent
firewall-cmd --reload
systemctl restart docker
```

这里说明一下如果开始 firewalld 服务被锁定`Unit is masked`

需要先解除锁定，然后才能开放端口

```
systemctl unmask firewall
```

# 开机启动

```
# 开机自启动
systemctl enable firewalld
systemctl enable docker
```

# 可能出现的问题

在配置阿里云Docker Yum源时候，可能出现`Loaded plugins: fastestmirror`的错误提示，百度上的解决如下：

1、

```
# vi  /etc/yum/pluginconf.d/fastestmirror.conf
enabled=0    //由 1 改成0 ，禁用该插件
verbose=0
always_print_best_host = true
socket_timeout=3
 
#  Relative paths are relative to the cachedir (and so works for users as well
# as root).
hostfilepath=timedhosts.txt
maxhostfileage=10
maxthreads=15
 
#exclude=.gov, facebook
 
#include_only=.nl,.de,.uk,.ie
```

2、

```
#vi /etc/yum.conf

[main]
cachedir=/var/cache/yum/$basearch/$releasever
keepcache=0
debuglevel=2
logfile=/var/log/yum.log
exactarch=1
obsoletes=1
gpgcheck=1
plugins=1 #将plugins的值修改为0
installonly_limit=5
```

3、

```
copy
$ yum clean dbcache
```

4、重新执行配置源和安装命令即可