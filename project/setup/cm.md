## CM安装

1. lion 检查各个软件
	- java 检查version、JAVA_HOME、PATH
	- python 检查是否是2.X版本
	- mysql 检查安全、是否启动等
	- Apache/其他 HTTP仓库是否开启
	- 其他问题
2. lion 开始安装CM server
	 - 安装 $ sudo rpm -ivh cloudera-manager-daemons cloudera-manager-server
	 ![daemons安装示例图](./setup_cloudera-manager-daemons.PNG)
	 ![server安装示例图](./setup_cloudera-manager-server.PNG)
	 - 关闭开机自启 $ sudo chkconfig cloudera-scm-server off 
	 ![关闭开机自启的示例图](./cloudera-scm-server_off.PNG)
	 - 关联数据库和CM $ sudo /usr/share/cmf/schema/scm_prepare_database.sh mysql cmserver cmserveruser password
	 ![关联数据库和CM的示例图](./scm_prepare_database.PNG)
	 - 显示“All done, your SCM database is configured correctly!”后，启动服务 $ sudo service cloudera-scm-server start (启动速度很慢，启动前可以虚拟机做个快照，以防启动过程出现意外，导致不得不去一个一个删掉启动时创建的一些数据，再重新开启服务)
	 - 查看日志 sudo tail -f /var/log/cloudera-scm-server/cloudera-scm-server.log
	 - 如果日志内出现7180，就可以用浏览器浏览http://lion:7180
	 ![CM_server启动的示例图1](./start_cloudera-scm-server_1.PNG)
	 ![CM_server启动的示例图2](./start_cloudera-scm-server_2.PNG)
3. 使用浏览器进入http://lion:7180 页面，准备安装Agent
	- 登录默认 账户:admin 密码:admin
	![Web界面截图](./web_login.PNG)
	- 接受“最终用户许可条款和条件”，点击继续
	- 选择Cloudera Enterprise的试用版（可以试用60天，结束后会自动退回普通版），继续
	- 输入hostname:elephant tiger horse monkey lion，然后search搜索，成功后继续
	![指定要管理的主机截图1](./specify_hostname_1.PNG)
	![指定要管理的主机截图1](./specify_hostname_2.PNG)
	- 进入“集群安装-选择存储库”界面
		1. 选择“使用Parcel”，点击更多选项
		![示例1](./select_base_1.PNG)
		2. 在弹出的界面中，删除所有远程URL
		![示例2](./select_base_2.PNG)
		3. 添加我们之前已经配置好的CDH包的HTTP仓库URL
		![示例3](./select_base_3.PNG)
		4. 点击保存更改，界面“CDH版本”处变化成我们自己的CDH包的版本，同时添加Cloudera Manager Agent的库
		![示例4](./select_base_4.PNG)
	- 继续，不要安装该处提示的JDK，因为前面我们已经安装过了
	- 继续，不启用单用户模式
	- 来到“集群安装-提供 SSH 登录凭据”页面
	- 设置已经配好SSH的用户，确保每台服务器该用户名都已配置好SSH认证。如果需要非root执行，需要每台服务器配置对应用户的“免密码执行sudo”权限（在/etc/sudoers中添加jerry   ALL=(ALL)       NOPASSWD:ALL）
	![提供 SSH 登录凭据截图](./set_ssh.PNG)
	- 点击继续，开始安装每个节点的Agent（此处最容易出问题的是yum本地源配置错误、CM依赖的其他安装包没安装正确）
	![安装Agent截图1](./install_agent_1.PNG)
	![安装Agent截图2](./install_agent_2.PNG)
	- 点击继续安装CDH的Parcel包
	![安装CDH的Parcel包截图](./install_parcel.PNG)
	- 点击继续，开始检查主机正确性
	![检查主机正确性截图](./node_check.PNG)
4. Get2EC2 VM浏览器 安装 hadoop集群 CDH
	- 点击Custom	Services，选择HDFS YARN(MR2 Included)
	- 按文档配置集群的HDFS、CMS、YARN，继续
	- 配置数据库地址、库名、用户、密码
	- 修改日志保存位置
	- 开始安装
	- 等待安装结束，进入网页Home界面
	```
	如果出现时间不同步，检查各台服务器
	ping 192.168.1.1 是否能ping通?
	sudo ntpstat 查看是否是synchronised
	如果不是，sudo service ntpd restart
	可能要等5min才能完成同步
	```
