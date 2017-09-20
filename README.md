# information

# 存放学习文档

## Centos7系统相关

### 1、  如何减少/home分区，扩大/root分区

``` 

把/home内容备份，然后将/home文件系统所在的逻辑卷删除，扩大/root文件系统，新建/home：
tar cvf /tmp/home.tar /home    #备份/home
umount /home    #卸载/home，如果无法卸载，先终止使用/home文件系统的进程
lvremove /dev/centos/home    #删除/home所在的lv
lvextend -L +50G /dev/centos/root    #扩展/root所在的lv，增加50G
xfs_growfs /dev/centos/root    #扩展/root文件系统
lvcreate -L 56G -n home centos    #重新创建home lv
mkfs.xfs /dev/centos/home    #创建文件系统
mount /dev/centos/home /home #挂载
df -h

```
