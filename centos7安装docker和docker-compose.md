centos7系统下

1、安装docker
yum install -y -q docker-ce
2、安装docker-compose

```
Docker-Compose是一个部署多个容器的简单但是非常必要的工具.

安装Docker-Compose之前，请先安装 python-pip

　　安装 python-pip
　　1、首先检查linux有没有安装python-pip包，终端执行 pip -V
[root@vm-50-151 network-scripts]# pip -V
-bash: pip: command not found
　　2、没有python-pip包就执行命令 yum -y install epel-release
[root@vm-50-151 network-scripts]# yum -y install epel-release
Loaded plugins: fastestmirror, langpacks
base                                                                                                                                                                                            | 3.6 kB  00:00:00    
extras                                                                                                                                                                                          | 3.4 kB  00:00:00    
updates                                                                                                                                                                                         | 3.4 kB  00:00:00    
(1/2): extras/7/x86_64/primary_db                                                                                                                                                               | 129 kB  00:00:05    
(2/2): updates/7/x86_64/primary_db                                                                                                                                                              | 3.6 MB  00:00:09    
Loading mirror speeds from cached hostfile
 * base: mirrors.aliyun.com
 * extras: mirrors.163.com
 * updates: mirrors.cn99.com
Resolving Dependencies
--> Running transaction check
---> Package epel-release.noarch 0:7-9 will be installed
--> Finished Dependency Resolution
 
Dependencies Resolved
 
=======================================================================================================================================================================================================================
 Package                                                  Arch                                               Version                                          Repository                                          Size
=======================================================================================================================================================================================================================
Installing:
 epel-release                                             noarch                                             7-9                                              extras                                              14 k
 
Transaction Summary
=======================================================================================================================================================================================================================
Install  1 Package
 
Total download size: 14 k
Installed size: 24 k
Downloading packages:
epel-release-7-9.noarch.rpm                                                                                                                                                                     |  14 kB  00:00:05    
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : epel-release-7-9.noarch                                                                                                                                                                             1/1
  Verifying  : epel-release-7-9.noarch                                                                                                                                                                             1/1
 
Installed:
  epel-release.noarch 0:7-9                                                                                                                                                                                           
 
Complete!
　　3、执行成功之后，再次执行yum -y install python-pip
　　
[root@vm-50-151 network-scripts]# yum install python-pip
Loaded plugins: fastestmirror, langpacks
epel/x86_64/metalink                                                                                                                                                                            | 7.3 kB  00:00:00    
epel                                                                                                                                                                                            | 4.7 kB  00:00:00    
(1/3): epel/x86_64/group_gz                                                                                                                                                                     | 261 kB  00:00:01    
epel/x86_64/updateinfo         FAILED                                                        54% [=============================================-                                     ] 165 kB/s | 3.9 MB  00:00:20 ETA
http://ftp.riken.jp/Linux/fedora/epel/7/x86_64/repodata/ed160c344c46b2ec8d800367326ceaf25560b1515a0603a1e33a795b8b6492a1-updateinfo.xml.bz2: [Errno 12] Timeout on http://ftp.riken.jp/Linux/fedora/epel/7/x86_64/repodata/ed160c344c46b2ec8d800367326ceaf25560b1515a0603a1e33a795b8b6492a1-updateinfo.xml.bz2: (28, 'Operation too slow. Less than 1000 bytes/sec transferred the last 30 seconds')
Trying other mirror.
(2/3): epel/x86_64/updateinfo                                                                                                                                                                   | 845 kB  00:00:10    
(3/3): epel/x86_64/primary_db                                                                                                                                                                   | 6.1 MB  00:01:05    
Loading mirror speeds from cached hostfile
 * base: mirrors.aliyun.com
 * epel: mirror01.idc.hinet.net
 * extras: mirrors.163.com
 * updates: mirrors.cn99.com
Resolving Dependencies
--> Running transaction check
---> Package python2-pip.noarch 0:8.1.2-5.el7 will be installed
--> Processing Dependency: python-setuptools for package: python2-pip-8.1.2-5.el7.noarch
--> Running transaction check
---> Package python-setuptools.noarch 0:0.9.8-7.el7 will be installed
--> Processing Dependency: python-backports-ssl_match_hostname for package: python-setuptools-0.9.8-7.el7.noarch
--> Running transaction check
---> Package python-backports-ssl_match_hostname.noarch 0:3.4.0.2-4.el7 will be installed
--> Processing Dependency: python-backports for package: python-backports-ssl_match_hostname-3.4.0.2-4.el7.noarch
--> Running transaction check
---> Package python-backports.x86_64 0:1.0-8.el7 will be installed
--> Finished Dependency Resolution
 
Dependencies Resolved
 
=======================================================================================================================================================================================================================
 Package                                                                 Arch                                       Version                                             Repository                                Size
=======================================================================================================================================================================================================================
Installing:
 python2-pip                                                             noarch                                     8.1.2-5.el7                                         epel                                     1.7 M
Installing for dependencies:
 python-backports                                                        x86_64                                     1.0-8.el7                                           base                                     5.8 k
 python-backports-ssl_match_hostname                                     noarch                                     3.4.0.2-4.el7                                       base                                      12 k
 python-setuptools                                                       noarch                                     0.9.8-7.el7                                         base                                     397 k
 
Transaction Summary
=======================================================================================================================================================================================================================
Install  1 Package (+3 Dependent packages)
 
Total download size: 2.1 M
Installed size: 9.1 M
Is this ok [y/d/N]: y
Downloading packages:
warning: /var/cache/yum/x86_64/7/epel/packages/python2-pip-8.1.2-5.el7.noarch.rpm: Header V3 RSA/SHA256 Signature, key ID 352c64e5: NOKEY===========-                                ]  0.0 B/s | 1.3 MB  --:--:-- ETA
Public key for python2-pip-8.1.2-5.el7.noarch.rpm is not installed
(1/4): python2-pip-8.1.2-5.el7.noarch.rpm                                                                                                                                                       | 1.7 MB  00:00:00    
(2/4): python-backports-1.0-8.el7.x86_64.rpm                                                                                                                                                    | 5.8 kB  00:00:05    
(3/4): python-setuptools-0.9.8-7.el7.noarch.rpm                                                                                                                                                 | 397 kB  00:00:05    
(4/4): python-backports-ssl_match_hostname-3.4.0.2-4.el7.noarch.rpm                                                                                                                             |  12 kB  00:00:06    
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                                                                  302 kB/s | 2.1 MB  00:00:07    
Retrieving key from file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7
Importing GPG key 0x352C64E5:
 Userid     : "Fedora EPEL (7) <epel@fedoraproject.org>"
 Fingerprint: 91e9 7d7c 4a5e 96f1 7f3e 888f 6a2f aea2 352c 64e5
 Package    : epel-release-7-9.noarch (@extras)
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7
Is this ok [y/N]: y
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : python-backports-1.0-8.el7.x86_64                                                                                                                                                                   1/4
  Installing : python-backports-ssl_match_hostname-3.4.0.2-4.el7.noarch                                                                                                                                            2/4
  Installing : python-setuptools-0.9.8-7.el7.noarch                                                                                                                                                                3/4
  Installing : python2-pip-8.1.2-5.el7.noarch                                                                                                                                                                      4/4
  Verifying  : python2-pip-8.1.2-5.el7.noarch                                                                                                                                                                      1/4
  Verifying  : python-setuptools-0.9.8-7.el7.noarch                                                                                                                                                                2/4
  Verifying  : python-backports-1.0-8.el7.x86_64                                                                                                                                                                   3/4
  Verifying  : python-backports-ssl_match_hostname-3.4.0.2-4.el7.noarch                                                                                                                                            4/4
 
Installed:
  python2-pip.noarch 0:8.1.2-5.el7                                                                                                                                                                                    
 
Dependency Installed:
  python-backports.x86_64 0:1.0-8.el7                           python-backports-ssl_match_hostname.noarch 0:3.4.0.2-4.el7                           python-setuptools.noarch 0:0.9.8-7.el7                         
 
Complete!
　　4、对安装好的pip进行升级 pip install --upgrade pip
[root@vm-50-151 network-scripts]# pip install --upgrade pip
Collecting pip
  Downloading pip-9.0.1-py2.py3-none-any.whl (1.3MB)
    100% |?..?..?..?..?..?..?..?..?..?..?..?..?..?..?..?..| 1.3MB 135kB/s
Installing collected packages: pip
  Found existing installation: pip 8.1.2
    Uninstalling pip-8.1.2:
      Successfully uninstalled pip-8.1.2
Successfully installed pip-9.0.1
　　至此，pip安装好了，执行pip -V 再次检查pip环境。

[root@vm-50-151 network-scripts]# pip -V
pip 9.0.1 from /usr/lib/python2.7/site-packages (python 2.7)
　　安装Docker-Compose
　　1.终端执行：pip install docker-compose

报错：ReadTimeoutError: HTTPSConnectionPool(host='pypi.python.org', port=443): Read timed out
　　解决：pip --default-timeout=200 install -U docker-compose
[root@vm-50-151 network-scripts]# pip --default-timeout=200 install -U docker-compose
Collecting docker-compose
  Using cached docker_compose-1.17.1-py2.py3-none-any.whl
Collecting websocket-client<1.0,>=0.32.0 (from docker-compose)
  Using cached websocket_client-0.44.0-py2.py3-none-any.whl
Collecting requests!=2.11.0,<2.12,>=2.6.1 (from docker-compose)
  Downloading requests-2.11.1-py2.py3-none-any.whl (514kB)
    100% |?..?..?..?..?..?..?..?..?..?..?..?..?..?..?..?..| 522kB 832kB/s
Collecting PyYAML<4,>=3.10 (from docker-compose)
  Downloading PyYAML-3.12.tar.gz (253kB)
    100% |?..?..?..?..?..?..?..?..?..?..?..?..?..?..?..?..| 256kB 1.7MB/s
Collecting dockerpty<0.5,>=0.4.1 (from docker-compose)
  Downloading dockerpty-0.4.1.tar.gz
Collecting ipaddress>=1.0.16; python_version < "3.3" (from docker-compose)
  Downloading ipaddress-1.0.18-py2-none-any.whl
Collecting docopt<0.7,>=0.6.1 (from docker-compose)
  Downloading docopt-0.6.2.tar.gz
Collecting backports.ssl-match-hostname>=3.5; python_version < "3.5" (from docker-compose)
  Downloading backports.ssl_match_hostname-3.5.0.1.tar.gz
Collecting enum34<2,>=1.0.4; python_version < "3.4" (from docker-compose)
  Downloading enum34-1.1.6-py2-none-any.whl
Collecting texttable<0.10,>=0.9.0 (from docker-compose)
  Downloading texttable-0.9.1.tar.gz
Collecting cached-property<2,>=1.2.0 (from docker-compose)
  Downloading cached_property-1.3.1-py2.py3-none-any.whl
Collecting docker<3.0,>=2.5.1 (from docker-compose)
  Downloading docker-2.6.1-py2.py3-none-any.whl (117kB)
    100% |?..?..?..?..?..?..?..?..?..?..?..?..?..?..?..?..| 122kB 2.8MB/s
Collecting jsonschema<3,>=2.5.1 (from docker-compose)
  Downloading jsonschema-2.6.0-py2.py3-none-any.whl
Collecting six<2,>=1.3.0 (from docker-compose)
  Downloading six-1.11.0-py2.py3-none-any.whl
Collecting docker-pycreds>=0.2.1 (from docker<3.0,>=2.5.1->docker-compose)
  Downloading docker_pycreds-0.2.1-py2.py3-none-any.whl
Collecting functools32; python_version == "2.7" (from jsonschema<3,>=2.5.1->docker-compose)
  Downloading functools32-3.2.3-2.zip
Installing collected packages: six, websocket-client, requests, PyYAML, dockerpty, ipaddress, docopt, backports.ssl-match-hostname, enum34, texttable, cached-property, docker-pycreds, docker, functools32, jsonschema, docker-compose
  Found existing installation: six 1.9.0
    Uninstalling six-1.9.0:
      Successfully uninstalled six-1.9.0
  Running setup.py install for PyYAML ... done
  Running setup.py install for dockerpty ... done
  Running setup.py install for docopt ... done
  Found existing installation: backports.ssl-match-hostname 3.4.0.2
    Uninstalling backports.ssl-match-hostname-3.4.0.2:
      Successfully uninstalled backports.ssl-match-hostname-3.4.0.2
  Running setup.py install for backports.ssl-match-hostname ... done
  Running setup.py install for texttable ... done
  Running setup.py install for functools32 ... done
Successfully installed PyYAML-3.12 backports.ssl-match-hostname-3.5.0.1 cached-property-1.3.1 docker-2.6.1 docker-compose-1.17.1 docker-pycreds-0.2.1 dockerpty-0.4.1 docopt-0.6.2 enum34-1.1.6 functools32-3.2.3.post2 ipaddress-1.0.18 jsonschema-2.6.0 requests-2.11.1 six-1.11.0 texttable-0.9.1 websocket-client-0.44.0
　　检查docker-compose 安装：docker-compose -version
[root@vm-50-151 network-scripts]# docker-compose -version
docker-compose version 1.17.1, build 6d101fb
　　

　　如果报错：
pkg_resources.DistributionNotFound: backports.ssl-match-hostname>=3.5 
　　解决方法：更新backports.ssl-match-hostname的版本，在终端输入命令
　　pip install --upgrade backports.ssl_match_hostname

　　如若python版本过低，需升级，见：http://www.cnblogs.com/YatHo/p/8257387.html
  
  ```
