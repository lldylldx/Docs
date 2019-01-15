#### 安装JDK

配置java环境变量

#### 安装KETTLE：

官方下载地址：http://community.pentaho.com/projects/data-integration/

下载完后，解压即可

#### 运行spoon

在不同的平台上运行spoon所支持的脚本：

Spoon.bat：在Windows平台上运行spoon；

Spoon.sh：在Linux、AppleOSX、Solaris平台上运行Spoon。

#### 配置JVM及内存配置问题

如果java_home设置了，仍提示：

 could not find the main class. Program will exit!

可以设置环境变量：PENTAHO_JAVA_HOME，变量值为：jdk的安装目录，1.6以上即可。本机为: D:\Program Files\java\jdk1.7.0_8



#### 如果启动还报错 ERROR：could not create the java virtual machine! 不是Java虚拟出了问题，修改一下spoon.bat里内存配置：
```
 if "%PENTAHO_DI_JAVA_OPTIONS%"=="" set PENTAHO_DI_JAVA_OPTIONS="-Xms1024m" "-Xmx2048m" "-XX:MaxPermSize=256m"
```
 

 改为：
```
 if "%PENTAHO_DI_JAVA_OPTIONS%"=="" set PENTAHO_DI_JAVA_OPTIONS="-Xms512m" "-Xmx1024m" "-XX:MaxPermSize=256m"
```
#### 连接数据库找不到驱动问题（MySql为例）

提示错误
```
[mysql] : org.pentaho.di.core.exception.KettleDatabaseException: 
      Error occured while trying to connect to the database
      Driver class 'org.gjt.mm.mysql.Driver' could not be found, make sure the 'MySQL' driver (jar file) is installed.
      org.gjt.mm.mysql.Driver
```

解决办法：把mysql-connector-java-5.1.37-bin.jar拷贝到

\\pdi-ce-6.0.1.0-386\data-integration\lib下面，然后重新启动spoon即可。
