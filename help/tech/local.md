### 1 概述

#### 1.1 部署方案

Worktile的私有部署方案是基于Docker来构建的，每个服务都会被打包成一个镜像，包含如下模块：  
在部署时，首先需要将如上的镜像下载下来，针对客户环境进行配置，然后启动，初始化数据，这样系统就可以运行了。  
![](/assets/5-1.png)

#### 1.2 部署方式

![](/assets/5-2.png)

#### 1.3 部署架构

![](/assets/5-3.png)

### 2 环境准备

#### 2.1 服务器

服务器数量与实际用户数相关。

##### 2.1.1 基础配置![](/assets/5-4.png)

##### 2.1.2 HA和LB服务器

需要如下资源较多  
1）CPU  
2）带宽

##### 2.1.3 App服务器

需要如下资源较多  
1）CPU  
2）内存  
3）带宽

##### 2.1.4 Cache服务器

需要如下资源较多  
1）内存  
2）CPU  
3）带宽

##### 2.1.5 Database服务器

需要如下资源较多  
1）CPU  
2）内存  
3）SSD硬盘  
4）带宽

#### 2.2操作系统及软件

![](/assets/5-5.png)

#### 2.3域名

如果是单服务架构，则可以不提供域名。  
如果需要启用https，则还需要提供证书文件，例如worktile.crt和worktile.key

* Web 
worktile.xxx.com
* Box 
worktile-box.xxx.com
* Hook 
worktile-hook.xxx.com
* IM 
worktile-im.xxx.com

#### 2.4 初始化数据信息

##### 2.4.1 管理员
* 邮箱
* 用户名
* 姓名
* 密码

##### 2.4.2 企业域名
也就是公有云版本的二级域名
#### 2.5 邮箱
* 邮箱账号信息
* STMP信息

#### 2.6 开发端口
![](/assets/5-6.png)
【重要提示】
* 通常情况下，为了保证您的数据可靠性，我们建议部署服务器数量为五台及五台以上，此举有利于数据之间相互备份，保证更高的可靠性；
* 用户需知晓由于单台服务器引发的数据可靠性方面的风险；
* 实际部署中服务器数量和技术架构方案，欢迎与Worktile运维工程师讨论决定；

### 3 逻辑框架
![](/assets/5-7.png)

### 4 物理框架
### 4.1 单服务架构
所有服务部署到一台服务器上，LB是可选项，可以不配置；
![](/assets/5-8.png)
#### 4.2 分布式
每种服务只启动一个实例，部署到不同的服务器上，LB是可选项，可以不配置；
![](/assets/5-9.png)
#### 4.3 负载均衡架构
将服务分别部署到不同服务器上，LB和App组成一组负载均衡集群，Cache和Database分别组成负载均衡集群。
![](/assets/5-10.png)
#### 4.4 高可用架构
增加两台HA服务器，同时可以增加LB服务器的数量，组成LB的负载均衡集群，当HA1出现故障时，会自动切换到HA2，同时对外提供服务的VIP也会随之切换到HA2上，从而增加系统的稳定性。
![](/assets/5-11.png)
### 5 系统功能
#### 5.1 提供的功能
1）消息（私聊，群聊以及系统消息）
2）项目（管理团队成员的工作，跟踪任务进展）
3）日历（随时安排公司会议，团队活动）
4）网盘（管理企业内部资料，随时与团队成员分享）
5）简报（跟进团队成员每日/周/月的工作）
6）审批（轻量级审批管理，支持自定义审批流程）
7）目标（目标展示／进度更新／周期管理／数据分析）
### 6 部署
#### 6.1 安装
##### 6.1.1 修改配置文件，设置ip地址等信息
* conf/apps/web/independence.js
* conf/apps/im/independence.js

##### 6.1.2 执行./install.sh开始安装
* 安装Docker
 
使用.deb文件安装

`script/install-docker-dpks.sh`
 使用apt-get安装
`script/install-docker-apt-get.sh`
* 环境初始化，设置数据目录，登陆docker registry，mongodb数据初始化

`script/init.sh`
* 下载镜像

`script/image-manager.sh`

* 启动服务

`script/run.sh`
* 初始化数据

`script/run-init-data.sh`

* 获取硬件信息

`script/get-hardware-info.sh`

##### 6.1.3 生成license
根据获取到的硬件信息生成license文件，并放到conf/apps/web/下
##### 6.1.4 重启web服务

`script/service-manager.sh --action=restart --services=web`

#### 6.2 维护
##### 6.2.1 服务
* 启动服务，会启动所有docker容器

`./start.sh`

* 停止服务，会停止所有docker容器

`./stop.sh`

* 重启服务，会先将docker容器停止，然后再启动

`./restart.sh`

* 清除服务，会先将docker容器停止，然后清除

`./remove.sh`

* 管理某个或某几个服务
运行

`./service-manager.sh --action=run --services="redis mongodb web"`
启动

`./service-manager.sh --action=start --services="redis mongodb web"`

停止

`./service-manager.sh --action=stop --services="redis mongodb web"`

重启

`./service-manager.sh --action=restart --services="redis mongodb` web"

清除

`./service-manager.sh --action="rm -v" --services="redis mongodb` web"

##### 6.2.2 数据及备份

一般建议放到/data目录下，包括数据文件和日志文件。
数据备份的时候，直接复制/data目录即可，如果只想备份数据文件，则只复制相应目录下的数据文件夹。

* Database

数据文件
mongodb/standalone/db
日志文件
mongodb/standalone/logs

* Cache
数据文件
redis/standalone/db
日志文件
redis/standalone/logs

* Search
数据文件
elasticsearch/db
日志文件
elasticsearch/logs

* Box
数据文件
seaweedfs

* LB
日志文件
nginx/logs

#### 6.2.3监控

* 定时监控脚本

在crontab中配置了监控脚本，每分钟会执行一次，如下：
/home/ubuntu/worktile/script/monitor-services.sh >> /home/ubuntu/worktile/script/monitor-services.sh.out 2>&1
当有服务所在的容器停下来的时候，该脚本监测到会将其启动起来。

* 后台日常检查

执行如下命令，检查服务的状态：
docker ps -a
会输出如下信息：
![](/assets/5-12.png)
查看STATUS的状态，UP表示在正常运行，Exited表示已经停止运行

* 前台模拟用户检查
在浏览器中打开网站，例如http://worktile.xxx.com，然后登陆系统检查
