

## 准备

Centos7

consul_1.8.0_linux_amd64.zip(https://www.consul.io/)



## 安装

创建目录

cd /usr/local/software

mkdir consul

上传

将安装包上传到consul目录

解压

unzip consul_1.8.0_linux_amd64.zip

安装

执行./consul即可



## 配置

开放8500端口

firewall-cmd --zone=public --add-port=8500/tcp --permanent

firewall-cmd --reload



## 启动

./consul agent -dev -ui -node=consul-dev -client=172.16.29.248

-ui是开启控制台页面

-client是consul部署服务器的ip



访问 http://ip:8500即可看到consul控制台