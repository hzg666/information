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
