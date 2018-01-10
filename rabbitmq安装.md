# 一、安装

## 1. ubuntu安装rabbitmq

```
echo 'deb http://www.rabbitmq.com/debian/ testing main' |   sudo tee /etc/apt/sources.list.d/rabbitmq.list
wget -O- https://www.rabbitmq.com/rabbitmq-release-signing-key.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get install rabbitmq-server
```

##  2. 启动RabbitMQ管理插件，用于web界面管理

```
rabbitmq-plugins enable rabbitmq_management
service rabbitmq-server restart
```

##  3. 测试安装完成的RabbitMQ

```
rabbitmqctl status
```

## 4. 添加用户并加入管理员

```
//添加用户和设定密码rabbitmqctl add_user User Password
rabbitmqctl add_user admin china-ops
//设为用户的角色为管理员rabbitmqctl set_user_tags User administrator
rabbitmqctl set_user_tags admin administrator
//设为用户的权限rabbitmqctl  set_permissions  -p  VHostPath  User  ConfP  WriteP  ReadP
rabbitmqctl  set_permissions -p /  admin '.*' '.*' '.*'  
```

## 5.url访问

```
http://192.168.237.166:15672/#/
```

# 二、使用


```
常用命令列举

应用管理

rabbitmqctl status //显示RabbitMQ中间件的所有信息
rabbitmqctl stop //停止RabbitMQ应用，关闭节点
rabbitmqctl stop_app //停止RabbitMQ应用
rabbitmqctl start_app //启动RabbitMQ应用
rabbitmqctl restart //重置RabbitMQ节点
rabbitmqctl force_restart //强制重置RabbitMQ节点

用户管理

rabbitmqctl add_user username password //添加用户
rabbitmqctl delete_user username //删除用户
rabbitmqctl change_password username newpassword //修改密码
rabbitmqctl list_users //列出所有用户


权限控制管理

rabbitmqctl add_vhost vhostpath //创建虚拟主机
rabbitmqctl delete_vhost vhostpath //删除虚拟主机
rabbitmqctl list_vhosts //列出所有虚拟主机
rabbitmqctl set_permissions [-p vhostpath] username <conf> <write> <read> //设置用户权限
rabbitmqctl clear_permissions [-p vhostpath] username //删除用户权限
rabbitmqctl list_permissions [-p vhostpath] //列出虚拟机上的所有权限
rabbitmqctl list_user_permissions username //列出用户权限

Web界面管理RabbitMQ

使用rabbitmq-plugins enable rabbitmq_management来启动Management插件。 默认是可以本地登录localhost:15672，用户名：guest；密码：guest；端口默认15672。
服务器nginx配置 
server {
listen 80;
index index.html index.htm;

# Make site accessible from http://localhost/

server_name rabbitmq.tlwlmy.com;

location / {
    # First attempt to serve request as file, then
    # as directory, then fall back to displaying a 404.
    # try_files $uri $uri/ =404;
    # Uncomment to enable naxsi on this location
    # include /etc/nginx/naxsi.rules
    proxy_pass http://127.0.0.1:15672;
}
}


修改RabbitMQ数据存储

复制RabbitMQ存储数据到/data/lib/rabbitmq，cp命令-p可以将文件属性也复制

sudo cp -R -p /var/lib/rabbitmq /data/lib/rabbitmq

添加RabbitMQ环境变量文件

sudo vim /etc/rabbitmq/rabbitmq-env.conf

rabbitmq-env.conf文件内容，修改完文件，重启RabbitMQ服务

RABBITMQ_MNESIA_BASE=/data/lib/rabbitmq/mnesia

服务器允许其他服务器使用RabbitMQ服务，由于guest默认是localhost使用的，需要另外创建用户给外部服务器使用，可以使用Web管理页面添加用户，也可以通过命令添加用

创建用户

sudo rabbitmqctl add_user tlwlmy tlwlmy

设置用户角色

sudo rabbitmqctl set_user_tags tlwlmy administrator

设置用户权限

sudo rabbitmqctl set_permissions -p "/" tlwlmy ".*" ".*" ".*"

设置完成后可以查看当前用户和角色(需要开启服务)

sudo rabbitmqctl list_users

其他服务器访问链接，192.168.1.3为部署RabbitMQ服务内部ip地址

amqp://tlwlmy:tlwlmy@192.168.1.3:5672//

python测试例子


#!/user/bin/env python


# encoding: utf-8


from celery import Celery
celery = Celery(broker='amqp://tlwlmy:tlwlmy@192.168.1.3:5672//')


# 发送

celery.send_task('rabbitmq_test', ({'test': 'test'},), queue='test', compression='zlib', serializer='json')

注意 
修改系统hostname后将会丢失旧数据和用户，需要重新添加用户

参考 
官方安装
官方配置
Networking and RabbitMQ
RabbitMQ安装和使用
设置RabbitMQ远程ip登录

http://blog.csdn.net/tianjiewang/article/details/58383062
```


