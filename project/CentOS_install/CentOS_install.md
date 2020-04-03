## CentOS 安装注意事项

1. 系统版本 6.5 x86_64 
    - 如果用的是VMware，新建虚拟机时，选择“自定义(高级)”、“稍后安装操作系统”
2. 虚拟机网络模式 NAT
3. 4台内存给4G，再选一台给6G做CM节点 (有条件的，更大好些)
4. 硬盘大小 30-50G
5. 语言选择 English
6. 可在安装界面配置静态IP，或者后续手动配置
7. 账户创建：一个root、一个普通用户
8. 分区： / 根分区一定要大，一定要大，一定要大！
9. 安装包选择(除默认外)
	- 勾选: FTP、Server服务、MySQL
	- 不勾选： java

## 安装教程参考 
- 地址: http://jingyan.baidu.com/article/25648fc1a235c99191fd0008.html
- 注意: 此链接仅供参考，具体注意事项请参考**上述的内容、下面的截图**

## 安装截图参考
- 选择 English

![选择 English截图](./select_english.png)

- 主机域名、网络配置

![主机域名、静态IP截图](./localhost_static_ip.png)

- 选择 编辑网卡eth0

![选择 编辑网卡eth0截图](./edit_eth0.png)

- 编辑网卡eth0 详细设置（IP、子网掩码、网关请参考自身网络设定）

![详细设置截图](./edit_detail.png)

- 选择自定义安装（尽量不要选Desktop，实际生产环境不需要UI桌面，可以选择Basic Server）
 
![自定义安装截图](./custom_package.png)

- 不勾选java

![去掉安装java截图](./select_un_java.png)

- 勾选MySQL
 
![安装MySQL截图](./select_mysql.png)

- 勾选FTP

![安装FTP截图](./select_FTP.png)

- 勾选web service

![安装web service截图](./select_web_service.png)
