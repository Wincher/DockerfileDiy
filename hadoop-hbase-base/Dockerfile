FROM ubuntu

LABEL author=wincher

ADD jdk-8u152-linux-x64.tar.gz /usr/java/
ADD hbase-1.4.0-bin.tar.gz /usr/local/
ADD hadoop-2.8.3.tar.gz /usr/local/
ADD zookeeper-3.5.2-alpha.tar.gz /usr/local/

ENV LANG en_US.UTF-8
ENV LC_ALL en_US.UTF-8
ENV JAVA_HOME=/usr/java/jdk1.8.0_152
ENV JRE_HOME=$JAVA_HOME/jre
ENV CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib

ENV ZOOKEEPER=/usr/local/zookeeper

ENV HADOOP_HOME=/usr/local/hadoop
ENV HADOOP_CONFIF_HOME=$HADOOP_HOME/etc/hadoop

ENV HBASE_HOME=/usr/local/hbase

ENV PATH=$PATH:$JAVA_HOME/bin:$HADOOP_HOME/bin:$HADOOP_HOME/sbin:$HBASE_HOME/bin:$ZOOKEEPER/home

RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak && \
mv /usr/local/hadoop-2.8.3 /usr/local/hadoop && \
mv /usr/local/hbase-1.4.0 /usr/local/hbase && \
mv /usr/local/zookeeper-3.5.2-alpha /usr/local/zookeeper
ADD sources.list /etc/apt

RUN  apt update
RUN apt install openssh-server openssh-client net-tools iputils-ping --assume-yes
RUN ssh-keygen -t rsa -f ~/.ssh/id_rsa -N '' && \
ssh-keygen -t dsa -f ~/.ssh/id_dsa -N ''  && \
cat ~/.ssh/id_rsa.pub >> authorized_keys && \
cat ~/.ssh/id_dsa.pub >> authorized_keys
