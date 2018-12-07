#### 1.6.1 安装
##### 1.6.1.1 修改配置文件，设置ip地址等信息
* conf/apps/web/independence.js
* conf/apps/im/independence.js

##### 1.6.1.2 执行./install.sh开始安装
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
  
##### 1.6.1.3 生成license

* 根据获取到的硬件信息生成license文件，并放到conf/apps/web/下

##### 1.6.1.4 重启web服务

* script/service-manager.sh --action=restart --services=web
