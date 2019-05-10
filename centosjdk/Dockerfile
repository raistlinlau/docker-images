FROM centos:7
MAINTAINER raistlin "<raistlinlau@gmail.com>"

#change repository to aliyun
RUN yum clean all && rm -rf /etc/yum.repos.d/*.repo
RUN curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
RUN curl -o /etc/yum.repos.d/epel.repo http://mirrors.aliyun.com/repo/epel-7.repo

RUN sed -i '/aliyuncs/d' /etc/yum.repos.d/CentOS-Base.repo
RUN sed -i '/aliyuncs/d' /etc/yum.repos.d/epel.repo
RUN sed -i 's/$releasever/7/g' /etc/yum.repos.d/CentOS-Base.repo

RUN yum clean all && yum makecache fast

#install jdk
RUN yum update -y && yum -y install java-1.8.0-openjdk.x86_64
# RUN java -version

# RUN /bin/echo -e "LANG=\"en_US.UTF-8\"" > /etc/default/local
# RUN /bin/echo -e "LANG=\"zh_CN.UTF-8\"" > /etc/default/local

#
RUN yum -y install kde-l10n-Chinese telnet
RUN yum -y reinstall glibc-common
RUN yum clean all

ENV LC_ALL zh_CN.utf8
RUN localedef -c -f UTF-8 -i zh_CN zh_CN.utf8
