### 部署

#### 安装
##### 1） 修改配置文件，设置ip地址等信息
* conf/apps/web/independence.js
* conf/apps/im/independence.js

##### 2） 执行./install.sh开始安装
* 安装Docker 
  使用.deb文件安装
  script/install-docker-dpks.sh
  使用apt-get安装
  script/install-docker-apt-get.sh
  
* 环境初始化，设置数据目录，登陆docker registry，mongodb数据初始化
  script/init.sh

* 下载镜像
  script/image-manager.sh

* 启动服务
  script/run.sh

* 初始化数据
  script/run-init-data.sh

* 获取硬件信息
  script/get-hardware-info.sh
  
##### 3） 生成license

* 根据获取到的硬件信息生成license文件，并放到conf/apps/web/下

##### 4） 重启web服务

* script/service-manager.sh --action=restart --services=web
####维护
##### 1） 服务
* 启动服务，会启动所有docker容器

 ./start.sh
* 停止服务，会停止所有docker容器
 
 ./stop.sh
* 重启服务，会先将docker容器停止，然后再启动
 
 ./restart.sh
* 清除服务，会先将docker容器停止，然后清除
 
 ./remove.sh
* 管理某个或某几个服务

  运行
  ./service-manager.sh --action=run --services="redis mongodb web"
  启动
  ./service-manager.sh --action=start --services="redis mongodb web"
  停止
  ./service-manager.sh --action=stop --services="redis mongodb web"
  重启
  ./service-manager.sh --action=restart --services="redis mongodb web"
  清除
  ./service-manager.sh --action="rm -v" --services="redis mongodb web"
  
##### 2） 数据及备份
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
  
##### 3）监控
* 定时监控脚本
  
  在crontab中配置了监控脚本，每分钟会执行一次，如下：
  /home/ubuntu/worktile/script/monitor-services.sh >> 
  /home/ubuntu/worktile/script/monitor-services.sh.out 2>&1
  当有服务所在的容器停下来的时候，该脚本监测到会将其启动起来
* 后台日常检查

  执行如下命令，检查服务的状态：
  docker ps -a
  会输出如下信息：
  # ![](/assets/6.2.3.jpg) 
  
  查看STATUS的状态，UP表示在正常运行，Exited表示已经停止运行
* 前台模拟用户检查

  在浏览器中打开网站，例如 http://worktile.xxx.com 然后登陆系统检查
 
