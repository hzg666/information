## 使用docker安装jenkins

```

### 生产部署环境：A:192.168.1.2　　B:192.168.1.3  两台服务器系统均是Centos 7.3 , Docker版本都1.12.6

### Jenkins安装操作步骤：

　　1.在A服务器上使用命令：docker pull jenkinsci/jenkins  获取到Docker镜像；

　　2.使用命令：docker run -p 8080:8080 -p 50000:50000 --name jenkins -u root -v /var/jenkins_home:/var/jenkins_home jenkinsci/jenkins:lts 生成名为jenkins的容器并运行，并以root用户身份将jenkins_home目录挂载到宿主机上，防止容器删除，数据丢失；

　　3.在输出的控制台信息中，一定要记得记录生成的秘钥串，待会要用到，如图所示：



 　　4.看到秘钥串生成，就可以打开浏览器，输入：http://192.168.1.2:8080 进入jenkins系统配置界面，输入刚刚记录的秘钥串，点继续



　　注意：如果出现打不开网页，请用命令docker ps -a 查看jenkins容器是否是up的，还有记得检查防火墙是否开放了8080和50000端口。

　　　　　附Centos 7开放端口相关命令：

　　　　　　　查看已经开放的端口：firewall-cmd --list-ports
　　　　　　　开启端口：firewall-cmd --zone=public --add-port=8080/tcp --permanent
　　　　　　　命令含义：
　　　　　　　　　　　　–zone #作用域

　　　　　　　　　　　　–add-port=80/tcp #添加端口，格式为：端口/通讯协议
　　　　　　　　　　　　–permanent #永久生效，没有此参数重启后失效
　　　　　　　重启防火墙：
　　　　　　　　　　firewall-cmd --reload                     #重新载入firewall配置，使配置生效
　　　　　　　　　　systemctl stop firewalld.service      #停止firewall
　　　　　　　　　　systemctl disable firewalld.service  #禁止firewall开机启动

　　5.下一步到了选择安装插件的界面，这里我们选择安装默认常用的插件，如图



 　　6.插件安装完成后，选择以admin管理员用户继续，如下图：



　　7.然后选择，如下图所圈的按钮继续

　　8.选择设置



　　9.把admin管理员账户的密码修改一下，然后点击保存，到此Jenkins安装结束。



 

Docker-build-step插件安装部署

　　1.打开系统管理，插件管理，找到Docker build step插件，勾选选中，点击直接安装，安装完成后重启一下Jenkins容器；

　  2.使用终端登录到B服务器，修改/usr/lib/systemd/system/docker.service 为：

     ExecStart=/usr/bin/dockerd-current -H tcp://0.0.0.0:4243 -H unix:///var/run/docker.sock \  参考下图：



　　注意：4243为端口号，只要不跟系统冲突，任意端口都行。修改完后执行以下两条命令使配置生效：systemctl daemon-reload和service docker restart ，防火墙一定要记得开放4243端口。

　　3.打开Jenkins Web系统界面，找到系统管理，系统设置，找到Docker Builer配置项，填入B服务器的IP地址和端口号，如图所示，点击测试连接，测试连接成功后，我们就可以利用Docker build step插件自动化管理Docker了。


Jenkinsci 使用文档：https://github.com/jenkinsci/docker/blob/master/README.md

Jenkinsci Docker Hub 地址：https://hub.docker.com/r/jenkinsci/jenkins/
```

https://www.cnblogs.com/soar1688/p/6833540.html
