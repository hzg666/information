# 1. ubuntu安装rabbitmq

```
echo 'deb http://www.rabbitmq.com/debian/ testing main' |   sudo tee /etc/apt/sources.list.d/rabbitmq.list
wget -O- https://www.rabbitmq.com/rabbitmq-release-signing-key.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get install rabbitmq-server
```

#  2. 启动RabbitMQ管理插件，用于web界面管理

```
rabbitmq-plugins enable rabbitmq_management
service rabbitmq-server restart
```

#  3. 测试安装完成的RabbitMQ

```
rabbitmqctl status
```
