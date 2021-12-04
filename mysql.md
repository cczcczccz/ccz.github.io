###
### 来源
> https://segmentfault.com/a/1190000041056206

> https://zhuanlan.zhihu.com/p/262721133

## Ubuntu20.04上安装MySQL8.0

### 1.更新源
- sudo apt-get update  #更新源
- sudo apt-get install mysql-server #安装

### 2.MySQL服务管理
- sudo service mysql status # 查看服务状态
- sudo service mysql start # 启动服务
- sudo service mysql stop # 停止服务
- sudo service mysql restart # 重启服务

### 3.登录，两种方式
1. 默认账户登录 
   - sudo cat /etc/mysql/debian.cnf #查看密码
   - mysql -u debian-sys-maint -p   登录
2. 直接登录
   - sudo mysql

### 4.创建root用户
1. 创建账户
   - create user 'root'@'%' identified by 'root';
2. 授权
   - GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' WITH GRANT OPTION;
3. 设密码
   - ALTER USER 'root'@'%' IDENTIFIED BY '你的密码';
4. 刷新权限
   - FLUSH PRIVILEGES;

### 5.允许远程访问
- 把/etc/mysql/mysql.conf.d/mysqld.cnf的bind-address=127.0.0.1 注释
- 如果提示readonly，换成root用户操作

### 6.重启服务
- service mysql restart