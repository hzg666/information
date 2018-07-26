# 使用DBeaver连接hive
介绍
在hive命令行beeline中写一些很长的查询语句不是很方便，查询结果也不是很友好，于是找了一个hive的客户端界面工具DBeaver，它也支持很多符合JDBC连接的数据库，例如MySQL、Oracle等。下载地址：http://dbeaver.jkiss.org/download/

连接
首先新建一个连接（可以看到支持的数据库非常多），选择Apache Hive，点击下一步。
![image](https://github.com/hzg666/information/blob/master/images/a1)

填写连接数据库的用户名、密码、地址、库等相关信息，然后点击编辑连接驱动。

![image](https://github.com/hzg666/information/blob/master/images/a2)


选择下载或更新。

![image](https://github.com/hzg666/information/blob/master/images/a3)


在这里一定要选择与自己hive版本（我这里是1.1.0）对应的连接驱动下载（这个选择版本的地方比较坑爹，找了半天），否则后面会有报错。

![image](https://github.com/hzg666/information/blob/master/images/a4)


这里可以填写连接名称和类型。

![image](https://github.com/hzg666/information/blob/master/images/a5)


最后点击test connection，没有问题可以保存关闭了。

![image](https://github.com/hzg666/information/blob/master/images/a6)


在界面最左侧可以看到我们刚刚设置保存的连接，右击connect。

![image](https://github.com/hzg666/information/blob/master/images/a7)


使用体验
接下来使用就比较简单了。右击选择编辑sql。

![image](https://github.com/hzg666/information/blob/master/images/a8)


在界面右侧上方是编辑区，下方是结果，举个例子：

![image](https://github.com/hzg666/information/blob/master/images/a9)


你也可以保存你的sql和result，还有挺多实用和便捷的功能，一款挺好用的db客户端。
