# Ubuntu系统资料

## 1、 修改ip配置

```
# vi /etc/network/interfaces

auto eth0
iface eth0 inet static
address 192.168.237.163
netmask 255.255.255.0
gateway 192.168.237.1

dns-nameservers 10.72.8.2 


# vi /etc/resolvconf/resolv.conf.d/base
nameserver 10.72.8.2

查看网络接口状态 ifconfig
关闭网卡 ifdown eth0
开启网卡 ifup eth0
```

## 2、 docker的安装与卸载
### 安装docker

```
 #wget -qO- https://get.docker.com/ | sh

```

### 卸载docker

```
 卸载Docker包：

 $ sudo apt-get purge docker-engine

卸载Docker包及其以来不再需要使用下面的命令：

 $ sudo apt-get autoremove --purge docker-engine

上面的命令不会移除镜像，容器，卷或者是用户创建的配置文件。如果你想删除所有的镜像，容器和卷，运行下面的命令：

 $ rm -rf /var/lib/docker

你必须手动删除用户创建的配置文件。

如果中断安装后，再安装出错，运行以下命令：
 dpkg --configure -a

```
