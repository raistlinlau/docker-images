# 基础镜像
# X86_64 OR amd64
FROM opstool/kylin:v10sp1-x86_64
# arm64
#FROM opstool/kylin:v10sp1-arm64
LABEL maintainer "jianxiong.liu <jianxiong.liu@suwell.cn>"

RUN uname -a && cat /etc/.productinfo

RUN yum update -y

#DEBIAN_FRONTEND=noninteractive

# 安装依赖 (可以扩展)
RUN yum install -y \
    qt-devel \
    make \
    git && \
    yum clean all
    
RUN ln -s /usr/lib64/qt4/bin/qmake /usr/bin/qmake

WORKDIR /home/build

CMD ["tail", "-f", "/dev/null"] 