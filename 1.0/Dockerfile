FROM centos:7
MAINTAINER selton "seltonzyf@outlook.com"
RUN set -x && \
yum install -y git && \
git config --global http.postBuffer 20M && \
mkdir -p /opt/psqueue && \
git clone https://gitee.com/selton/PSQueueServer.git /opt/psqueue && \
yum install -y java-1.8.0-openjdk-devel.x86_64 && \
sed -i '$a\export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.222.b10-1.el7_7.x86_64' /etc/profile && \
sed -i '$a\JRE_HOME=$JAVA_HOME/jre' /etc/profile && \
sed -i '$a\CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH' /etc/profile && \
sed -i '$a\PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$PATH' /etc/profile && \
source  /etc/profile && \
yum install -y dos2unix && \
dos2unix /opt/psqueue/bin/psqueue.sh && \
sed -i '23c   export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.222.b10-1.el7_7.x86_64' /opt/psqueue/bin/psqueue.sh
