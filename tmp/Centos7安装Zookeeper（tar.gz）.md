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







### 安装







### 配置









### 测试







## 集群版

### 准备







### 安装







### 配置









### 测试









