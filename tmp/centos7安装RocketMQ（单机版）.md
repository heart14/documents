# centos7安装RocketMQ（单机版）

## 准备

Centos7

RocketMQ二进制版 （rocketmq-all-4.7.1-bin-release.zip）



## 安装

### 创建目录

```bash
cd /usr/local/software
mkdir rocketmq
```



### 上传安装包

![rocketmq1](C:\Users\jayhe\Pictures\rocketmq1.png)

### 解压安装

```bash
unzip rocketmq-all-4.7.1-bin-release.zip
mv rocketmq-all-4.7.1-bin-release rocketmq-4.7.1
```

![rocketmq2](C:\Users\jayhe\Pictures\rocketmq2.png)

![rocketmq3](C:\Users\jayhe\Pictures\rocketmq3.png)



## 配置

默认配置中的jvm虚拟机内存设置比较高，可以设置小一点，否则可能会无法启动

### 进入bin目录

````bash
cd /usr/local/software/rocketmq/rocketmq-4.7.1/bin
````

### 修改namesrv配置

````bash
vim runserver.sh
````

![rocketmq4](C:\Users\jayhe\Pictures\rocketmq4.png)

![rocketmq5](C:\Users\jayhe\Pictures\rocketmq5.png)

### 修改broker配置

```bash
vim runbroker.sh
```

![rocketmq6](C:\Users\jayhe\Pictures\rocketmq6.png)



## 启动

### 进入到bin目录

````bash
cd /usr/local/software/rocketmq/rocketmq-4.7.1/bin
````

### 先启动namesrv

````bash
nohup sh mqnamesrv &
````

![rocketmq7](C:\Users\jayhe\Pictures\rocketmq7.png)

查看日志

````bash
tail -f ~/logs/rocketmqlogs/namesrv.log
````

![rocketmq8](C:\Users\jayhe\Pictures\rocketmq8.png)



### 再启动broker

````bash
nohup sh mqbroker -n localhost:9876 &
````

![rocketmq9](C:\Users\jayhe\Pictures\rocketmq9.png)

查看日志

````bash
tail -f ~/logs/rocketmqlogs/broker.log
````

![rocketmq10](C:\Users\jayhe\Pictures\rocketmq10.png)

注意：

启动broker时要指定namesrv的ip和端口



## 关闭

### 进入bin目录

````bash
cd /usr/local/software/rocketmq/rocketmq-4.7.1/bin
````

### 关闭broker

````bash
sh mqshutdown broker
````

### 关闭namesrv

```bash
sh mqshutdown namesrv
```

