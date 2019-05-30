### 使用DockerFile 生成docker image
docker build -t centos:sshd . <br/>

### 以新创建的镜像新建容器
docker run -d -p 10022:22 -p 18080:8080 -p 18081:8081 -p 18088:8088 -p 50070:50070 --add-host master:172.17.0.2 --add-host slave1:172.17.0.3 --add-host slave2:172.17.0.4 --name master centos:spark /usr/local/sbin/run.sh<br/>
docker run -d -p 20022:22 -p 28081:8081 --add-host master:172.17.0.2 --add-host slave1:172.17.0.3 --add-host slave2:172.17.0.4 --name slave1 centos:spark /usr/local/sbin/run.sh<br/>
docker run -d -p 30022:22 -p 38081:8081 --add-host master:172.17.0.2 --add-host slave1:172.17.0.3 --add-host slave2:172.17.0.4 --name slave2 centos:spark /usr/local/sbin/run.sh<br/>

### 如何从本机登录
$ sudo ssh root@127.0.0.1 -p 10022<br/>

### master上启动hadoop 
对hdfs进行格式化<br/>
/opt/hadoop/bin/hadoop namenode -format<br/>
在namenode上执行启动命令<br/>
/opt/hadoop/sbin/start-yarn.sh<br/>
启动Spark<br/>
/opt/spark/sbin/start-all.sh<br/>