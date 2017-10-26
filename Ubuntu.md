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

wget wget http://apache.communilink.net/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.tar.gz
解压

tar -xzf apache-maven-3.3.9-bin.tar.gz
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

## 4、 ubuntu下安装gedit插件

```

因为gedit-plugins : 依赖: gir1.2-zeitgeist-2.0

所以首先
sudo apt-get install gir1.2-zeitgeist-2.0
 如果报错可以先
sudo apt-get update
 然后
sudo apt-get install gedit-plugins
 在gedit的插件里面选中嵌入终端、单词补全等插件就行
 
 ```
 
 ##  5、 Ubuntu 安装 JDK 7 / JDK8 的两种方式

```

ubuntu 安装jdk 的两种方式:
1:通过ppa(源) 方式安装.

2:通过官网下载安装包安装.

这里推荐第1种,因为可以通过 apt-get upgrade 方式方便获得jdk的升级

使用ppa/源方式安装
1.添加ppa

sudo add-apt-repository ppa:webupd8team/java

sudo apt-get update
2.安装oracle-java-installer

　jdk7

sudo apt-get install oracle-java7-installer
　jdk8

sudo apt-get install oracle-java8-installer
安装器会提示你同意 oracle 的服务条款,选择 ok

然后选择yes 即可

如果你懒,不想自己手动点击.也可以加入下面的这条命令,默认同意条款:

JDK7 默认选择条款

echo oracle-java7-installer shared/accepted-oracle-license-v1-1 select true | sudo /usr/bin/debconf-set-selections
JDK8 默认选择条款

echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | sudo /usr/bin/debconf-set-selections
 接下会是等待(依个人网速定)

如果你因为防火墙或者其他原因,导致installer 下载速度很慢,可以中断操作.然后下载好相应jdk的tar.gz 包,放在:

   /var/cache/oracle-jdk7-installer             (jdk7) 

   /var/cache/oracle-jdk8-installer              (jdk8) 

下面,然后安装一次installer. installer 则会默认使用 你下载的tar.gz包

3.设置系统默认jdk

JDk7

sudo update-java-alternatives -s java-7-oracle
JDK8

sudo update-java-alternatives -s java-8-oracle
如果即安装了jdk7,又安装了jdk8,要实现两者的切换,可以:

　　jdk8 切换到jdk7

sudo update-java-alternatives -s java-7-oracle
　　jdk7 切换到jdk8

sudo update-java-alternatives -s java-8-oracle
4.测试jdk 是是否安装成功:

java -version

javac -version
直接下载jdk压缩包方式安装(这里只介绍jdk7的,jdk8 的原理完全一致)
　分为下面5个步骤

   1.官网下载JDK

   2.解压缩,放到指定目录

   3.配置环境变量

   4.设置系统默认JDK

　5. 测试jdk

1.官网下载JDK　　　

     地址: http://www.oracle.com/technetwork/articles/javase/index-jsp-138363.html
　　选择相应的 .gz包下载 

2. 解压缩,放到指定目录(以jdk-7u60-linux-x64.gz为例)

　　创建目录:

sudo mkdir /usr/lib/jvm
　加压缩到该目录:

 sudo tar -zxvf jdk-7u60-linux-x64.gz -C /usr/lib/jvm
3.修改环境变量:　　

sudo vim ~/.bashrc
　文件的末尾追加下面内容:

#set oracle jdk environment
export JAVA_HOME=/usr/lib/jvm/jdk1.7.0_60  ## 这里要注意目录要换成自己解压的jdk 目录
export JRE_HOME=${JAVA_HOME}/jre  
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib  
export PATH=${JAVA_HOME}/bin:$PATH  
　使环境变量马上生效

 source ~/.bashrc
4.设置系统默认jdk 版本

sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.7.0_60/bin/java 300  
sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk1.7.0_60/bin/javac 300  
sudo update-alternatives --install /usr/bin/jar jar /usr/lib/jvm/jdk1.7.0_60/bin/jar 300   
sudo update-alternatives --install /usr/bin/javah javah /usr/lib/jvm/jdk1.7.0_60/bin/javah 300   
sudo update-alternatives --install /usr/bin/javap javap /usr/lib/jvm/jdk1.7.0_60/bin/javap 300   
　然后执行:

sudo update-alternatives --config java
    若是初次安装jdk,会有下面的提示     

   There is only one alternative in link group java (providing /usr/bin/java): 
    /usr/lib/jvm/jdk1.7.0_60/bin/java

　否者,选择合适的jdk

5.测试jdk

java -version

java version "1.7.0_60"
  Java(TM) SE Runtime Environment (build 1.7.0_60-b19)
  Java HotSpot(TM) 64-Bit Server VM (build 24.60-b09, mixed mode)

  jdk 安装成功

ubuntu  两种下安装jdk7 jdk8 的方式介绍完毕

 参考文章: 

 1. http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html
 2. http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html
 
```

## 6、 安装phpmyadmin

```
1）安装mysql
2）安装phpmyadmin
sudo apt-get install phpmyadmin
3）切换到/var/www/html
cd /var/www/html
sudo ln -s /usr/share/phpmyadmin phpmyadmin
4）打开浏览器
http://192.168.237.171（服务器ip）/phpmyadmin/
```

## 7、 linux 使用dpkg 安装和卸载“xxx.deb”包
```
如果ubuntu要安装新软件，已有deb安装包（例如：iptux.deb），但是无法登录到桌面环境。那该怎么安装？答案是：使用dpkg命令。
dpkg命令常用格式如下：
sudo dpkg -I iptux.deb#查看iptux.deb软件包的详细信息，包括软件名称、版本以及大小等（其中-I等价于--info）
sudo dpkg -c iptux.deb#查看iptux.deb软件包中包含的文件结构（其中-c等价于--contents）
sudo dpkg -i iptux.deb#安装iptux.deb软件包（其中-i等价于--install）
sudo dpkg -l iptux#查看iptux软件包的信息（软件名称可通过dpkg -I命令查看，其中-l等价于--list）
sudo dpkg -L iptux#查看iptux软件包安装的所有文件（软件名称可通过dpkg -I命令查看，其中-L等价于--listfiles）
sudo dpkg -s iptux#查看iptux软件包的详细信息（软件名称可通过dpkg -I命令查看，其中-s等价于--status）
sudo dpkg -r iptux#卸载iptux软件包（软件名称可通过dpkg -I命令查看，其中-r等价于--remove）
```
