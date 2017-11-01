## 配置HTTP协议仓库
我们默认在封闭的网络内部安装集群，将parcel包放置在HTTP协议仓库，可以让ClouderaManager命令Agent去下载内部HTTP仓库的文件。这样免去了手动分发到各个节点的麻烦。

### 操作(选择在lion部署）
1. 如果按照之前的CentOS安装步骤，那么系统是默认自带Apache HTTP服务的
	- Apache HTTP下载地址：http://httpd.apache.org/download.cgi
2. 开启httpd服务 $ service httpd start
3. 尝试使用浏览器访问其Web UI界面 例如：http://owo
4. 将下载的cm和cdh都存到/var/www/html下
5. 使用浏览器访问http仓库 http://owo/cm 和 http://owo/cdh

### 操作截图
- 开启httpd服务

![开启httpd服务](./httpd_start.png)

- Apache界面

![Apache界面](./http_web_ui.png)

- http仓库cm

![http仓库cm](./http_cm.png)

- http仓库cdh

![http仓库cdh](./http_cdh.png)
