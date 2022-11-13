# https://hub.docker.com/_/mysql
# https://github.com/docker-library/mysql/tree/master/5.7
FROM mysql:5.7.31

# 配置apt阿里云镜像
RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak \
	&& echo "deb http://mirrors.aliyun.com/debian/ buster main non-free contrib" > /etc/apt/sources.list \
	&& echo "deb http://mirrors.aliyun.com/debian-security buster/updates main" >> /etc/apt/sources.list \
	&& echo "deb http://mirrors.aliyun.com/debian/ buster-updates main non-free contrib" >> /etc/apt/sources.list \ 
	&& echo "deb http://mirrors.aliyun.com/debian/ buster-backports main non-free contrib" >> /etc/apt/sources.list

# 设置时区
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

# 安装系统调试工具
RUN apt-get update --allow-insecure-repositories --allow-unauthenticated
RUN apt-get install -y \
	htop \
	vim \
	tree \
	net-tools 

# 拷贝配置文件
COPY conf/mysqld.cnf /etc/mysql/mysql.conf.d/mysqld.cnf

# 镜像信息
LABEL Author="Spark Lee"
LABEL Description="MySQL Community Server 5.7"
