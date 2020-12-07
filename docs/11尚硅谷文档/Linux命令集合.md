

[TOC]



# 一、linux指令

```
free -m：内存
su root：切换
sudo yum install -y yum-utils：安装
sudo mkdir -p /etc/docker：创建文件夹


```



# 二、docker



```
1、卸载旧版本【uninstall old versions】
	yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
                  
2、安装相关依赖
sudo yum install -y yum-utils

3、设置镜像地址
	sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
推荐使用阿里镜像：
	sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo【这个镜像和后面提到的镜像加速不同，这里指的是下载docker本身的镜像地址】
	
4、安装docker【INSTALL DOCKER ENGINE】
sudo yum install docker-ce docker-ce-cli containerd.io

5、启动docker
sudo systemctl start docker
虚拟机开机启动：sudo systemctl enable docker

6、测试
docker images
```



```
1、查看已启动镜像：docker images
2、查看所有镜像：docker images -a
3、启动docker：sudo systemctl start docker
4、虚拟机开机启动：sudo systemctl enable docker
5、docker启动后启动容器：sudo docker update mysql --restart=always
6、重启容器，例如mysql：
	查看容器的id或name：docker ps -a
	重启restart id或name【重启就代表启动了】：
		docker restart 1b4671904bfa
		docker restart mysql
7、终止容器：docker stop redis
8、删除容器：docker rm redis
9、进入容器的运行时环境
进入mysql：docker exec -it mysql /bin/bash
进入redis：docker exec -it redis redis-cli
whereis mysql
10、退出容器运行时环境：exit
11、虚拟机开机自动启动mysql：sudo docker update mysql --restart=always

```

## 安装mysql

```
1、去hub.docker.com查看版本，然后:加上版本，否则会下载最新版本

2、sudo docker pull mysql:5.7

3、启动容器并设置相关参数
docker run -p 3306:3306 --name mysql \
-v /mydata/mysql/log:/var/log/mysql \
-v /mydata/mysql/data:/var/ib/mysql \
-v /mydata/mysql/conf:/etc/mysql \
-e MYSQL_ROOT_PASSWORD=root \
-d mysql:5.7

    参数说明
    -p 3306:3306:将容器的3306端口映射到主机的3306端口
    -v /mydata/mysql/conf:/etc/mysql:将配置文件夹挂载到主机【linux文件与容器内部的文件挂载】
    -v /mydata/mysql/log:/var/log/mysgl:将日志文件夹挂载到主机【不用进入到容器内部就能查看日志】
    -v /mydata/mysql/data:/var/ib/mysql/:将配置文件夹挂载到主机【相当于快捷方式】
    -e MYSQL_ROOT_PASSWORD=root: 初始化root用户的密码
   	-d 后台启动

4、远程无法连接mysql：密码没有修改
【https://blog.csdn.net/scarecrow__/article/details/81556845】
	1）docker exec -it mysql /bin/bash进入mysql
	2）连入mysql：mysql -uroot -proot
	3）查询：select host,user,plugin,authentication_string from mysql.user;
		找到user为root的两列，
			%：表示不限制ip的配置
			localhost：表示本地连接的配置
			plugin数据非mysql_native_password表示要修改密码
		执行以下语句：
		ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'root';

5、远程无法连接mysql：修改root用户远程访问权限
	“password”填写密码 root
grant all privileges on *.* to root@"%" identified by "password" with grant option;

6、在linux的 mydata/mysql/conf/my.cnf配置文件下加入下【这一步的作用不知道是干啥~】
[client]
default-character-set=utf8

[mysql]
default-character-set=utf8
[mysqld]
init_connect='SET collation_connection = utf8_unicode_ci'
init_connect='SET NAMES utf8'
character-set-server=utf8
collation-server=utf8_unicode_ci
skip-character-set-client-handshake
skip-name-resolve

7、重启：docker restart mysql

8、虚拟机开机自动启动mysql容器
	sudo docker update mysql --restart=always
```

## 安装redis

```
1、去hub.docker.com查看版本，然后:加上版本，否则会下载最新版本

2、docker pull redis【拉取最新镜像】

3、新建redis配置文件夹：
	mkdir -p /mydata/redis/conf

4、新建redis配置文件：
	touch /mydata/redis/conf/redis.conf
	
5、开启持久化
vim /mydata/redis/conf/redis.conf
添加：appendonly yes

6、驱动容器，并挂载相关配置、端口
docker run -p 6379:6379 --name redis \
-v/mydata/redis/data:/data \
-v/mydata/redis/conf/redis.conf:/etc/redis/redis.conf \
-d redis redis-server /etc/redis/redis.conf

7、终止容器：docker stop redis
8、删除容器：docker rm redis

9、连接：
	方式1：进入容器运行时环境连接
	docker exec -it redis /bin/bash
	redis-cli -p 6379
	方式2：默认连接name是redis的容器，默认找6379端口
	docker exec -it redis redis-cli 
	方式3：windows可视化客户端直接连接6379端口
	
10、自动启动redis：sudo docker update redis --restart=always
```

