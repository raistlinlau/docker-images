FROM raistlinlau/centos7-jdk1.8
MAINTAINER raistlin "<raistlinlau@gmail.com>"

RUN cd /root
RUN wget http://dl.mycat.io/1.6-RELEASE/Mycat-server-1.6-RELEASE-20161028204710-linux.tar.gz
RUN tar -zxvf Mycat-server-1.6-RELEASE-20161028204710-linux.tar.gz mycat

ENV MYCAT_HOME=/root/mycat
ENV PATH=$PATH:${MYCAT_HOME}/bin

RUN chmod u+x /root/mycat
EXPOSE 8066 9066
CMD ["/root/mycat", "console"]
