阿里云服务器安装指南 

---

## 1.apache-tomcat安装说明-Mac

1. 下载apache-tomcat-8.5.75.tar.gz

2. 下载jdk-8u321-linux-x64.tar.gz 
   
   [Apache Tomcat&reg; - Apache Tomcat 8 Software Downloads](https://tomcat.apache.org/download-80.cgi)

3. 下载FileZilla，登陆阿里云服务器
   
   1. 在usr目录中创建java
      
      1. 在java目录中分别创建jdk与tomcat目录
      
      2. /usr/java/jdk与/usr/java/tomcat传输jdk-8u321-linux-x64.tar.gz与 apache-tomcat-8.5.75.tar.gz

4. 打开终端
   
   1. ssh root@阿里云服务器ip
   
   2. 输入阿里云服务器密码
   
   3. 在jdk目录下输入：tar -zxvf jdk-8u321-linux-x64.tar.gz
      
      1. 解压文件
      
      2. 解压完成后退回到根目录
         
         1. vim  /etc/profile, 输入i进行编辑
            
            #set java environment
            
            export JAVA_HOME=/usr/java/jdk/jdk1.8.0_321
            
            export JRE_HOME=/usr/java/jdk/jdk1.8.0_321/jre
            
            export CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH
            
            export PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$JAVA_HOME:$PATH
         
         2. 然后按Esc键  再按shift和 ; 键 输入 wq! 进行保存
         
         3. 输入source /etc/profile
         
         4. 输入java -version 检查是否成功
   
   4. 在tomcat目录下输入：tar -zxvf apache-tomcat-8.5.75.tar.gz
      
      1. 解压文件
      
      2. 解压完成后，进入到apache-tomcat-8.5.75的bin文件夹下：cd /usr/java/tomcat/apache-tomcat-8.5.41/bin
         
         1. 写入配置 vim setclasspath.sh
         
         2. 在文件的最后写入
            
            export JAVA_HOME=/usr/java/jdk/jdk1.8.0_321
            export JRE_HOME=/usr/java/jdk/jdk1.8.0_321/jre
         
         3. 按Esc键  再按shift和 ; 键 输入 wq! 进行保存
         
         4. 在cd /usr/java/tomcat/apache-tomcat-8.5.24/bin 目录下执行  ./startup.sh
            
             

---

## 配置站点默认路由页面

1. 打开tomcat-1.8\conf下的server.xml文件
   
   1. 添加（<Context path="" docBase="example" reloadable="true"/>），docBase=站点目录

2. 打开tomcat-1.8\conf下的web.xml文件
   
   1. 修改默认页面名称

3. 打开tomcat-1.8\bin
   
   1. 开启tomcat服务器：执行：./startup.sh
   
   2. 关闭tomcat服务器：执行：./shutdown.sh
