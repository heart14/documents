# Centos7安装Zookeeper（*.tar.gz）

## 单机版

### 准备

Centos7

Zookeeper安装包（官网地址https://zookeeper.apache.org/）





### 安装

mkdir /usr/local/software/zookeeper-single

将安装包上传到该目录下

解压安装包

tar -zxvf apach-zookeeper-3.6.1.tar.gz

重命名文件夹

mv apach-zookeeper-3.6.1-bin zookeeper-3.6.1





### 配置

在解压后的目录下新建data目录

cd zookeeper-3.6.1

mkdir data



进入conf目录，修改配置文件

cd conf

复制一份zoo_sample.cfg到zoo.cfg

cp zoo_sample.cfg zoo.cfg

编辑文件，把里面dataDir处改为刚才创建的data目录路径

vim zoo.cfg

然后保存退出







### 测试

进入bin目录

cd bin

运行zookeeper

./zkServer.sh start



查看zookeeper状态

./zkServer.sh status



停止zookeeper

./zkServer.sh stop









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









