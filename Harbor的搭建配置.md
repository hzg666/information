# Harbor的搭建配置

## 1、Harbor 介绍
Docker容器应用的开发和运行离不开可靠的镜像管理，虽然Docker官方也提供了公共的镜像仓库，但是从安全和效率等方面考虑，部署我们私有环境内的Registry也是非常必要的。Harbor是由VMware公司开源的企业级的Docker Registry管理项目，它包括权限管理(RBAC)、LDAP、日志审核、管理界面、自我注册、镜像复制和中文支持等功能。

## 2、部署方法：
  操作系统：Ubuntu16
  
### (1)安装docker： 
命令：#wget -qO- https://get.docker.com/ | sh

### (2)安装docker-com：
参照：https://docs.docker.com/compose/install/#install-compose

```
命令：
# sudo curl -L https://github.com/docker/compose/releases/download/1.17.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
# sudo chmod +x /usr/local/bin/docker-compose
# docker-compose -v 
```

### (3)安装Harbor：

```
3.1、克隆源码：
# git clone https://github.com/vmware/harbor
```
