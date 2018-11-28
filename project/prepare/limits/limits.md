## 修改可打开的文件上限

Linux默认可以打开的文件数量最大数量是1024，作为大数据服务器，多数程序需要大量打开文件，默认的数值显然是不够，我们需要做适当的调整（例如修改至65536）。

### 查看当前系统限制
- $ ulimit -a 命令查看各种限制
- open files 这一行即为可打开的最大文件数量值（默认1024）

### 修改可打开的文件上限
- $ vim /etc/security/limits.conf
- 修改用户jeryy的限制
  - jerry soft nofile 65536
  - jeryy hard nofile 65536
- 修改所有用户的限制（推荐只做单个用户的修改，不做全部的修改）
  - \* soft nofile 65536
  - \* hard nofile 65536
