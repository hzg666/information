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


##  3、 安装maven

### 安装环境

```
操作系统：Ubuntu 14.04.1 server amd64
```

### 安装jdk
```

在安装maven之前，必须确保已经安装过jdk。

安装jdk的方法请参考文章《Ubuntu 14.04.1中安装JDK》 http://www.linuxidc.com/Linux/2015-03/114618.htm。
```

### 下载maven
```

wget http://apache.fayea.com/apache-mirror/maven/maven-3/3.2.3/binaries/apache-maven-3.2.3-bin.tar.gz
解压

tar -xzf apache-maven-3.2.3-bin.tar.gz
设置环境变量

环境变量分为用户变量和系统变量。

用户变量配置文件：~/.bashrc（在当前用户主目录下的隐藏文件，可以通过`ls -a`查看到）

系统环境配置文件：/etc/profile

用户变量和系统变量的配置方法一样，本文以配置用户变量为例。

编辑配置文件.bashrc：

vi .bashrc
在文件末尾追加：

$ set maven environment
export M2_HOME=/home/Hadoop/apache-maven-3.2.3
export PATH=$M2_HOME/bin:$PATH
使环境变量生效

source .bashrc
验证

验证maven是否安装成功。

$ mvn --version
Apache Maven 3.2.3 (33f8c3e1027c3ddde99d3cdebad2656a31e8fdf4; 2014-08-12T04:58:10+08:00)
Maven home: /home/hadoop/apache-maven-3.2.3
Java version: 1.7.0_67, vendor: Oracle Corporation
Java home: /home/hadoop/jdk1.7.0_67/jre
Default locale: en_US, platform encoding: UTF-8
OS name: "linux", version: "3.13.0-32-generic", arch: "amd64", family: "unix"

```
