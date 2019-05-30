### 使用DockerFile 生成docker image
docker build -t centos:sshd . <br/>

### 以新创建的镜像新建容器
docker run -d -p 10022:22 --name master centos:sshd /usr/local/sbin/run.sh<br/>
docker run -d -p 10023:22 --name slave1 centos:sshd /usr/local/sbin/run.sh<br/>
docker run -d -p 10024:22 --name slave2 centos:sshd /usr/local/sbin/run.sh<br/>

### 如何从本机登录
$ sudo ssh root@127.0.0.1 -p 10022<br/>