FROM centos:7
MAINTAINER raistlin "<raistlinlau@gmail.com>"

#change repository to aliyun
RUN yum clean all && rm -rf /etc/yum.repos.d/*.repo
RUN curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
RUN curl -o /etc/yum.repos.d/epel.repo http://mirrors.aliyun.com/repo/epel-7.repo

RUN sed -i '/aliyuncs/d' /etc/yum.repos.d/CentOS-Base.repo
RUN sed -i '/aliyuncs/d' /etc/yum.repos.d/epel.repo
RUN sed -i 's/$releasever/7/g' /etc/yum.repos.d/CentOS-Base.repo

#RUN yum clean all && yum makecache fast

RUN yum -y install kde-l10n-Chinese telnet
RUN yum -y reinstall glibc-common

RUN yum clean all && yum makecache fast

ENV LC_ALL zh_CN.utf8
RUN localedef -c -f UTF-8 -i zh_CN zh_CN.utf8

RUN yum -y install libaio && yum -y install net-tools

RUN yum -y install wget
RUN wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
RUN rpm -ivh mysql-community-release-el7-5.noarch.rpm
RUN yum install mysql-server -y

RUN rm -rf /var/lib/mysql && mkdir -p /var/lib/mysql /var/run/mysqld
RUN chown -R mysql:mysql /var/lib/mysql /var/run/mysqld && chmod 777 /var/run/mysqld
VOLUME /var/lib/mysql


EXPOSE 3306 33060
CMD ["mysqld"]

#docker run -p 3306:3306 --name ws-mysql -v /root/myfile/mysql/conf:/etc/mysql/conf.d -v /root/myfile/mysql/logs:/logs -v /root/myfile/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=1@3$5^ -d centos-mysql57