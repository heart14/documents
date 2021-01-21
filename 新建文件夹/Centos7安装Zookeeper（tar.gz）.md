# Centos7安装Zookeeper（*.tar.gz）

## 单机版

### 准备

Centos7

Zookeeper安装包（apache-zookeeper-3.6.2-bin.tar）

Zookeeper官网地址https://zookeeper.apache.org/





### 安装

#### 新建目录

```bash
cd /usr/local/software
mkdir zookeeper-single
```



#### 上传安装包

将安装包上传到上一步所创建目录



#### 解压安装包

```bash
cd /usr/local/software/zookeeper-single
tar -zxvf apache-zookeeper-3.6.2-bin.tar
```













### 配置

#### 创建数据文件夹

```bash
cd apache-zookeeper-3.6.2-bin
mkdir data
```



#### 创建配置文件

```bash
#进入conf文件夹，将zoo_sample.cfg复制一份，重命名为zoo.cfg
/usr/local/software/zookeeper-single/apache-zookeeper-3.6.2-bin/conf
cp zoo_sample.cfg zoo.cfg
```



#### 编辑配置文件

```bash
vim zoo.cfg
```

将dataDir值改为前面所创建的data目录，:wq保存





### 测试

#### zookeeper服务端

##### 运行zookeeper

```bash 
cd /bin
./zkServer.sh start
```



##### 查看zookeeper状态

```bash
./zkServer.sh status
或者
ps -ef|grep zookeeper
```



##### 停止zookeeper

```bash
./zkServer.sh stop
```



#### zookeeper客户端

##### 运行zkCli

```bash
./zkCli.sh
```



### 注意事项

#### 启动报错



#### 问题日志 

Failed to bind to /0.0.0.0:8080

Address already in use



#### 解决方法

参考链接 http://roc.havemail.cn/archives/770.html







## 伪集群版

### 准备

伪集群版是在同一台服务器上，使用不同端口安装zookeeper服务器，来模拟多台zookeeper服务器

zookeeper集群至少需要三台服务器



### 安装

新建目录

zookeeper-server1

上传安装包

解压安装包

复制两份

zookeeper-server2

zookeeper-server3





### 配置

分别在三个server目录下新建data logs目录

编辑zoo.cfg

分别修改各自dataDir和dataLogDir

分别修改各自clientPort为不同端口

分别在配置文件底部加上集群配置

```bash
#cluster config
server.1=172.16.29.94:2887:3887
server.2=172.16.29.94:2888:3888
server.3=172.16.29.94:2889:3889
```

分别在各自data目录下新建myid文件

内容为集群配置中server.x的x

开放防火墙相应端口





## 集群版

### 准备

集群版是在多台服务器上安装zookeeper服务器





### 安装

同单机版





### 配置

同伪集群版，不同之处在于zoo.cfg中的集群配置那里写各服务器的ip

如

```bash
#cluster config
server.1=172.16.29.94:2888:3888
server.2=172.16.29.95:2888:3888
server.3=172.16.29.96:2888:3888
```

其它同为集群版









