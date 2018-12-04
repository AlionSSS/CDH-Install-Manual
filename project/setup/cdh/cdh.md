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
 
3. 如果不小心跳出了集群服务安装页面，请看这里
  - 访问lion的CM管理界面，例如 http://192.168.0.205:7180/cmf/home
  - 点击左上角的 Add Services
  ![点击安装服务截图](./cm_unknown.PNG)
  - 出现步骤2的界面
