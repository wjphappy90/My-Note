# 运维常用的150命令

| 命令                                      | 功能说明                                                     |
| :---------------------------------------- | :----------------------------------------------------------- |
| 线上查询及帮助命令(2个)                   |                                                              |
| man                                       | 查看命令帮助，命令的词典，更复杂的还有info，但不常用。       |
| help                                      | 查看Linux内置命令的帮助，比如cd命令。                        |
| 文件和目录操作命令(18个)                  |                                                              |
| ls                                        | 全拼list，功能是列出目录的内容及其内容属性信息。             |
| cd                                        | 全拼change directory，功能是从当前工作目录切换到指定的工作目录。 |
| cp                                        | 全拼copy，其功能为复制文件或目录。                           |
| find                                      | 查找的意思，用于查找目录及目录下的文件。                     |
| mkdir                                     | 全拼make directories，其功能是创建目录。                     |
| mv                                        | 全拼move，其功能是移动或重命名文件。                         |
| pwd                                       | 全拼print working directory，其功能是显示当前工作目录的绝对路径。 |
| rename                                    | 用于重命名文件。                                             |
| rm                                        | 全拼remove，其功能是删除一个或多个文件或目录。               |
| rmdir                                     | 全拼remove empty directories，功能是删除空目录。             |
| touch                                     | 创建新的空文件，改变已有文件的时间戳属性。                   |
| tree                                      | 功能是以树形结构显示目录下的内容。                           |
| basename                                  | 显示文件名或目录名。                                         |
| dirname                                   | 显示文件或目录路径。                                         |
| chattr                                    | 改变文件的扩展属性。                                         |
| lsattr                                    | 查看文件扩展属性。                                           |
| file                                      | 显示文件的类型。                                             |
| md5sum                                    | 计算和校验文件的MD5值。                                      |
| 查看文件及内容处理命令（21个）            |                                                              |
| cat                                       | 全拼concatenate，功能是用于连接多个文件并且打印到屏幕输出或重定向到指定文件中。 |
| tac                                       | tac是cat的反向拼写，因此命令的功能为反向显示文件内容。       |
| more                                      | 分页显示文件内容。                                           |
| less                                      | 分页显示文件内容，more命令的相反用法。                       |
| head                                      | 显示文件内容的头部。                                         |
| tail                                      | 显示文件内容的尾部。                                         |
| cut                                       | 将文件的每一行按指定分隔符分割并输出。                       |
| split                                     | 分割文件为不同的小片段。                                     |
| paste                                     | 按行合并文件内容。                                           |
| sort                                      | 对文件的文本内容排序。                                       |
| uniq                                      | 去除重复行。oldboy                                           |
| wc                                        | 统计文件的行数、单词数或字节数。                             |
| iconv                                     | 转换文件的编码格式。                                         |
| dos2unix                                  | 将DOS格式文件转换成UNIX格式。                                |
| diff                                      | 全拼difference，比较文件的差异，常用于文本文件。             |
| vimdiff                                   | 命令行可视化文件比较工具，常用于文本文件。                   |
| rev                                       | 反向输出文件内容。                                           |
| grep/egrep                                | 过滤字符串，三剑客老三。                                     |
| join                                      | 按两个文件的相同字段合并。                                   |
| tr                                        | 替换或删除字符。                                             |
| vi/vim                                    | 命令行文本编辑器。                                           |
| 文件压缩及解压缩命令（4个）               |                                                              |
| tar                                       | 打包压缩。oldboy                                             |
| unzip                                     | 解压文件。                                                   |
| gzip                                      | gzip压缩工具。                                               |
| zip                                       | 压缩工具。                                                   |
| 信息显示命令（11个）                      |                                                              |
| uname                                     | 显示操作系统相关信息的命令。                                 |
| hostname                                  | 显示或者设置当前系统的主机名。                               |
| dmesg                                     | 显示开机信息，用于诊断系统故障。                             |
| uptime                                    | 显示系统运行时间及负载。                                     |
| stat                                      | 显示文件或文件系统的状态。                                   |
| du                                        | 计算磁盘空间使用情况。                                       |
| df                                        | 报告文件系统磁盘空间的使用情况。                             |
| top                                       | 实时显示系统资源使用情况。                                   |
| free                                      | 查看系统内存。                                               |
| date                                      | 显示与设置系统时间。                                         |
| cal                                       | 查看日历等时间信息。                                         |
| 搜索文件命令（4个）                       |                                                              |
| which                                     | 查找二进制命令，按环境变量PATH路径查找。                     |
| find                                      | 从磁盘遍历查找文件或目录。                                   |
| whereis                                   | 查找二进制命令，按环境变量PATH路径查找。                     |
| locate                                    | 从数据库 (/var/lib/mlocate/mlocate.db) 查找命令，使用updatedb更新库。 |
| 用户管理命令（10个）                      |                                                              |
| useradd                                   | 添加用户。                                                   |
| usermod                                   | 修改系统已经存在的用户属性。                                 |
| userdel                                   | 删除用户。                                                   |
| groupadd                                  | 添加用户组。                                                 |
| passwd                                    | 修改用户密码。                                               |
| chage                                     | 修改用户密码有效期限。                                       |
| id                                        | 查看用户的uid,gid及归属的用户组。                            |
| su                                        | 切换用户身份。                                               |
| visudo                                    | 编辑/etc/sudoers文件的专属命令。                             |
| sudo                                      | 以另外一个用户身份（默认root用户）执行事先在sudoers文件允许的命令。 |
| 基础网络操作命令（11个）                  |                                                              |
| telnet                                    | 使用TELNET协议远程登录。                                     |
| ssh                                       | 使用SSH加密协议远程登录。                                    |
| scp                                       | 全拼secure copy，用于不同主机之间复制文件。                  |
| wget                                      | 命令行下载文件。                                             |
| ping                                      | 测试主机之间网络的连通性。                                   |
| route                                     | 显示和设置linux系统的路由表。                                |
| ifconfig                                  | 查看、配置、启用或禁用网络接口的命令。                       |
| ifup                                      | 启动网卡。                                                   |
| ifdown                                    | 关闭网卡。                                                   |
| netstat                                   | 查看网络状态。                                               |
| ss                                        | 查看网络状态。                                               |
| 深入网络操作命令（9个）                   |                                                              |
| nmap                                      | 网络扫描命令。                                               |
| lsof                                      | 全名list open files，也就是列举系统中已经被打开的文件。      |
| mail                                      | 发送和接收邮件。                                             |
| mutt                                      | 邮件管理命令。                                               |
| nslookup                                  | 交互式查询互联网DNS服务器的命令。                            |
| dig                                       | 查找DNS解析过程。                                            |
| host                                      | 查询DNS的命令。                                              |
| traceroute                                | 追踪数据传输路由状况。                                       |
| tcpdump                                   | 命令行的抓包工具。                                           |
| 有关磁盘与文件系统的命令（16个）          |                                                              |
| mount                                     | 挂载文件系统。                                               |
| umount                                    | 卸载文件系统。                                               |
| fsck                                      | 检查并修复Linux文件系统。                                    |
| dd                                        | 转换或复制文件。                                             |
| dumpe2fs                                  | 导出ext2/ext3/ext4文件系统信息。                             |
| dump                                      | ext2/3/4文件系统备份工具。                                   |
| fdisk                                     | 磁盘分区命令，适用于2TB以下磁盘分区。                        |
| parted                                    | 磁盘分区命令，没有磁盘大小限制，常用于2TB以下磁盘分区。      |
| mkfs                                      | 格式化创建Linux文件系统。                                    |
| partprobe                                 | 更新内核的硬盘分区表信息。                                   |
| e2fsck                                    | 检查ext2/ext3/ext4类型文件系统。                             |
| mkswap                                    | 创建Linux交换分区。                                          |
| swapon                                    | 启用交换分区。                                               |
| swapoff                                   | 关闭交换分区。                                               |
| sync                                      | 将内存缓冲区内的数据写入磁盘。                               |
| resize2fs                                 | 调整ext2/ext3/ext4文件系统大小。                             |
| 系统权限及用户授权相关命令（4个）         |                                                              |
| chmod                                     | 改变文件或目录权限。                                         |
| chown                                     | 改变文件或目录的属主和属组。                                 |
| chgrp                                     | 更改文件用户组。                                             |
| umask                                     | 显示或设置权限掩码。                                         |
| 查看系统用户登陆信息的命令（7个）         |                                                              |
| whoami                                    | 显示当前有效的用户名称，相当于执行id -un命令。               |
| who                                       | 显示目前登录系统的用户信息。                                 |
| w                                         | 显示已经登陆系统的用户列表，并显示用户正在执行的指令。       |
| last                                      | 显示登入系统的用户。                                         |
| lastlog                                   | 显示系统中所有用户最近一次登录信息。                         |
| users                                     | 显示当前登录系统的所有用户的用户列表。                       |
| finger                                    | 查找并显示用户信息。                                         |
| 内置命令及其它（19个）                    |                                                              |
| echo                                      | 打印变量，或直接输出指定的字符串                             |
| printf                                    | 将结果格式化输出到标准输出。                                 |
| rpm                                       | 管理rpm包的命令。                                            |
| yum                                       | 自动化简单化地管理rpm包的命令。                              |
| watch                                     | 周期性的执行给定的命令，并将命令的输出以全屏方式显示。       |
| alias                                     | 设置系统别名。                                               |
| unalias                                   | 取消系统别名。                                               |
| date                                      | 查看或设置系统时间。                                         |
| clear                                     | 清除屏幕，简称清屏。                                         |
| history                                   | 查看命令执行的历史纪录。                                     |
| eject                                     | 弹出光驱。                                                   |
| time                                      | 计算命令执行时间。                                           |
| nc                                        | 功能强大的网络工具。                                         |
| xargs                                     | 将标准输入转换成命令行参数。                                 |
| exec                                      | 调用并执行指令的命令。                                       |
| export                                    | 设置或者显示环境变量。                                       |
| unset                                     | 删除变量或函数。                                             |
| type                                      | 用于判断另外一个命令是否是内置命令。                         |
| bc                                        | 命令行科学计算器                                             |
| 系统管理与性能监视命令(9个)               |                                                              |
| chkconfig                                 | 管理Linux系统开机启动项。                                    |
| vmstat                                    | 虚拟内存统计。                                               |
| mpstat                                    | 显示各个可用CPU的状态统计。                                  |
| iostat                                    | 统计系统IO。                                                 |
| sar                                       | 全面地获取系统的CPU、运行队列、磁盘 I/O、分页（交换区）、内存、 CPU中断和网络等性能数据。 |
| ipcs                                      | 用于报告Linux中进程间通信设施的状态，显示的信息包括消息列表、共享内存和信号量的信息。 |
| ipcrm                                     | 用来删除一个或更多的消息队列、信号量集或者共享内存标识。     |
| strace                                    | 用于诊断、调试Linux用户空间跟踪器。我们用它来监控用户空间进程和内核的交互，比如系统调用、信号传递、进程状态变更等。 |
| ltrace                                    | 命令会跟踪进程的库函数调用,它会显现出哪个库函数被调用。      |
| 关机/重启/注销和查看系统信息的命令（6个） |                                                              |
| shutdown                                  | 关机。                                                       |
| halt                                      | 关机。                                                       |
| poweroff                                  | 关闭电源。                                                   |
| logout                                    | 退出当前登录的Shell。                                        |
| exit                                      | 退出当前登录的Shell。                                        |
| Ctrl+d                                    | 退出当前登录的Shell的快捷键。                                |
| 进程管理相关命令（15个）                  |                                                              |
| bg                                        | 将一个在后台暂停的命令，变成继续执行 （在后台执行）。        |
| fg                                        | 将后台中的命令调至前台继续运行。                             |
| jobs                                      | 查看当前有多少在后台运行的命令。                             |
| kill                                      | 终止进程。                                                   |
| killall                                   | 通过进程名终止进程。                                         |
| pkill                                     | 通过进程名终止进程。                                         |
| crontab                                   | 定时任务命令。                                               |
| ps                                        | 显示进程的快照。                                             |
| pstree                                    | 树形显示进程。                                               |
| nice/renice                               | 调整程序运行的优先级。                                       |
| nohup                                     | 忽略挂起信号运行指定的命令。                                 |
| pgrep                                     | 查找匹配条件的进程。                                         |
| runlevel                                  | 查看系统当前运行级别。                                       |
| init                                      | 切换运行级别。                                               |
| service                                   | 启动、停止、重新启动和关闭系统服务，还可以显示所有系统服务的当前状态。 |

# Linux命令小记

rpm -q xx 查询xx是否安装
yum install xx 安装xx软件包
yum remove xx 卸载xx软件包
vim /路径 读写文件
i：编辑模式
Exc：退出到命令模式
:wq：保存并退出Vim
startx （一次性地）从命令行切换到桌面环境
systemctl get-default 获取当前启动模式
systemctl set-default graphical.target 修改启动模式为图形化
systemctl set-default multi-user.target 修改启动模式为命令行
安装桌面环境 安装桌面环境（这里安装 GNOME）
systemctl start xx 启动xx服务
systemctl enable xx 开机自启动xx服务
firewall-cmd --permanent --zone=public --add-port=3389/tcp 防火墙开放3389端口
firewall-cmd --reload 重启防火墙
systemctl stop firewalld 关闭防火墙
systemctl disable firewalld
禁止防火墙开机启动

cp /路径 复制文件
systemctl daemon-reload
让服务文件修改生效

netstat -lnpt|grep xx 查看xx的服务端口

sudo yum update -y 更新服务器地软件包

sudo yum install java-1.8.0-openjdk -y 安装 OpenJRE

java -version 检测jre是否安装成功

sudo useradd -m halo 创建一个低权限地用户halo

sudo su halo 登录用户halo

wget url 下载xx安装包

useradd [-d home] [-s shell] [-c comment] [-m [-k template]] [-f inactive] [-e expire ] [-p passwd] [-r] name useradd或adduser命令用来建立用户帐号和创建用户的起始目录，使用权限是超级用户

主要参数

-c：加上备注文字，备注文字保存在passwd的备注栏中。
-d：指定用户登入时的主目录，替换系统默认值/home/<用户名>
-D：变更预设值。
-e：指定账号的失效日期，日期格式为MM/DD/YY，例如06/30/12。缺省表示永久有效。
-f：指定在密码过期后多少天即关闭该账号。如果为0账号立即被停用；如果为-1则账号一直可用。默认值为-1.
-g：指定用户所属的群组。值可以使组名也可以是GID。用户组必须已经存在的，期默认值为100，即users。
-G：指定用户所属的附加群组。
-m：自动建立用户的登入目录。
-M：不要自动建立用户的登入目录。
-n：取消建立以用户名称为名的群组。
-r：建立系统账号。
-s：指定用户登入后所使用的shell。默认值为/bin/bash。
-u：指定用户ID号。该值在系统中必须是唯一的。0~499默认是保留给系统用户账号使用的，所以该值必须大于499。
https://www.cnblogs.com/irisrain/p/4324593.html

w # whoami 查看当前登陆用户

 12:10:27 up 21:13,  1 user,  load average: 0.00, 0.01, 0.08
USER          TTY      FROM                 LOGIN@   IDLE   JCPU   PCPU WHAT
root            pts/0    ***.**.***.**    11:33    0.00s  0.08s  0.00s   w
tmp_3254  ps1       ***.**.***.**     11:33    0.00s  0.08s  0.00s   ls
su xxx # 或者直接 exit 退出当前用户登录，进入一个有管理员权限的用户

pkill -kill -t [TTY] 强制退出已经登陆用户

 0pkill -kill -t ps1
ls -a # ls --all 查看当前目录下的所有文件

service xx restart 重启xx应用

curl -o /路径 --create-dirs url 下载配置文件、模板等文件

sudo nginx -t 检查Nginx配置是否有误

sudo nginx -s reload 重载Nginx配置

sudo service xx status 查看xx的运行状态

sudo service halo stop 停止xx

sudo service halo restart 重启xx

sudo service halo start 启动xx

sudo systemctl daemon-reload 修改service文件之后需要刷新Systemd

sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo 添加软件源信息

sudo yum makecache fast 更新yum缓存

镜像加速

新建 daemon.json 文件

sudo vim /etc/docker/daemon.json
将下面的配置复制进去即可：

{
  "registry-mirrors": ["http://hub-mirror.c.163.com"]
}
注意：修改完配置文件之后需要执行 service docker restart 才可生效。

sudo docker pull ruibaby/xx 拉取xx的最新镜像

docker run --rm -it -d --name halo -p 8090:8090 -v ~/.halo:/root/.halo ruibaby/halo 创建容器并运行halo

--rm：停止之后自动删除容器。
--name：容器名。
-p：占用端口，前者为宿主机端口，后者为 Halo 的运行端口，可在 application.yaml 配置。
-v：目录映射，一般不要修改。
netstat -tln # netstat -tln | grep 8080 查找被占用的端口（可接特定端口号）

netstat -ntlp 查看其他端口

lsof -i:8060 查看端口属于哪个程序、端口被哪个进程占用

kill -9 进程id 杀掉占用端口的进程 根据pid杀掉

shutdown -h now 立即关机

shutdown -r now # reboot 立即重启

docker run --name some-wordpress --link some-mysql:mysql -d wordpress 参数说明：

--name 容器的的名字
--link 和其他容器做连接
-d/--detach 后台运行
docker run -d --privileged=true --name myMysql -v /data/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -p 33306:3306 mysql:5.6 参数解释：

-p: 端口映射，33306表示宿主，3306表示容器中的端口。 这里表示将宿主机的33306映射给镜像的3306.
-e: 环境变量， 环境变量和具体的Docker容器制作时设置有关，这里表示设置镜像中MySQL的root 密码时123456
-v: 指定数据卷，也就是将我们MySQL容器的/var/lib/mysql映射到宿主机的/data/mysql
--privileged=true: CentOS系统下的安全Selinux禁止了一些安全权限，导致MySQL容器在运行时会因为权限不足而报错，所以需要增加该选项
docker ps -a 查看MySQL是否正常运行

docker stop 容器名 停止运行

docker rm 容器名 删除容器（之后去掉-d选项重新运行排查错误）

快速批量删除docker镜像或容器

Docker本身并没有提供批量删除的功能，当有大量的镜像或者容器需要删除的时候，手动的一个一个删就比较麻烦了。

直接删除所有镜像或容器

    # 直接删除所有镜像
    docker rmi `docker images -q`
     
    # 直接删除所有容器
    docker rm `docker ps -aq`

按条件筛选之后删除

    # 按条件筛选之后删除镜像
    docker rmi `docker images | grep xxxxx | awk '{print $3}'`
     
    # 按条件筛选之后删除容器
    docker rm `docker ps -a | grep xxxxx | awk '{print $1}'`