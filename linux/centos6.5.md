
## 添加普通用户到sudoer
```
vi /etc/sudoers
拷贝root all all
修改为ijvm all all
```

## vmware克隆后网络问题
```
ifconfig -a 查看是eth0还是eth1
然后去到/etc//etc/sysconfig/network-scripts/ifcfg-eth1文件中
删掉网卡物理，修改ip

service network restart
```

## 修改主机名
```
vi /etc/sysconfig/network
```

## 创建用户
```
useradd -m ijvm
passwd ijvm
```


## 一些必须的命令
```
yum install -y lrzsz
yum -y install openssh-server
yum -y install openssh-clients
```


## 更改yum源
```
cd /etc/yum.repos.d
mv CentOS-Base.repo CentOS-Base.repo.bak

//更新为阿里云的源
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-6.repo

yum clean all
yum makecache
```
## NAT连接外网
```
vi /etc/sysconfig/network-scripts/ifcfg-eth1
修改为：
DEVICE=eth1
HWADDR=00:0C:29:4B:69:B3
TYPE=Ethernet
UUID=a4f1fefe-ac65-4131-b885-678d1d34bf7c
ONBOOT=yes
NM_CONTROLLED=yes
BOOTPROTO=static
IPADDR=172.16.6.5
NETMASK=255.255.255.0
GATEWAY=172.16.6.2
DNS1=172.16.6.2

service network restart
```