# win10x64-mysql
win10系统64位安装配置mysql解压版

1、在安装mysql的路径下面新建一个my.ini文件；
2、修改my.ini文件的内容如下：
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8
  
[mysqld]
#设置3306端口
port = 3306
# 设置mysql的安装目录
basedir=D:\mysql\mysql
# 设置mysql数据库的数据的存放目录，（新版mysql目录下没有data文件夹，但这里设置还是写上data存放目录）
datadir=D:\mysql\mysql\data  
# 允许最大连接数
max_connections=200
# 服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB

3、添加系统环境变量：
  在系统环境变量中新建MYSQL_HOME,值为mysql解压目录，例如：D:\mysql\mysql
  修改系统变量Path，新增%MYSQL_HOME%\bin
4、注册mysql服务
  打开cmd，进入d:\mysql\mysql\bin目录下执行命令：mysqld install MySQL --defaults-file="D:\mysql\mysql\my.ini"
5、初始化data目录
  在cmd命令窗口运行mysqld --initialize-insecure --user=mysql来生成mysql目录下的data目录，并创建好默认数据库，初始用户名为root，密码为空
6、启动服务
  在cmd窗口输入net start mysql来启动mysql服务
  输入mysql -u root -p进入mysql
  show databases;命令查看数据库列表
7、修改数据库密码
  set password=password('123456');
  flush privileges;
8、关闭mysql服务
  cmd窗口运行net stop mysql
