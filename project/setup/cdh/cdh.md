## CDH 安装

1. 开始安装CDH
  - 点击继续，安装CDH的Parcel包
  ![安装CDH的Parcel包截图](./install_parcel.PNG)
  - 点击继续，开始检查主机正确性
  ![检查主机正确性截图](./node_check.PNG)
2. 安装集群服务
  - 选择要安装的服务组合(这里我选择的Spark)
  ![服务组合截图](./select_service.PNG)
  - 定义角色分配，我们先默认安装Cloudera自动推荐的分配即可，不做改动
  ![定义角色分配](./decision_roles.PNG)
  - 继续，开始配置数据库设置
  - 数据库主机要对应之前安装MySQL的节点
  - 库名、用户、密码请参照前面[MySQL安装与准备](../../prepare/mysql/mysql.md)建库建用户的SQL语句
  - 配置好后，点击右下角的“测试连接”，无误后方可点击继续
  ![配置数据库设置截图](./conf_database.PNG)
  - 继续，来到“审核更改”处。
  - 此处采用默认值，不做修改。点击每行旁边的“？”，会有相应配置的提示。
  ![审核更改截图](./examine_change.PNG)
  - 点击继续，开始“首次运行”，等待依次启动各个服务
  ![首次运行截图1](./cdh_first_run_1.PNG)
  - 各个服务启动完毕^_^
  ![首次运行截图2](./cdh_first_run_2.PNG)
  - 点击继续，完成 :)
  ![完成截图](./cdh_run_over.PNG)
 
3. <font color='red'>如果不小心跳出了集群服务安装页面，请看这里</font>
  - 访问lion的CM管理界面，例如 http://192.168.0.205:7180/cmf/home
  - 点击左上角的 Add Services
  ![点击安装服务截图](./cm_unknown.PNG)
  - 出现步骤2的界面
