FROM cloudesire/java:7

MAINTAINER lemon

# Default to UTF-8 file.encoding
ENV LANG=C.UTF-8

# 创建临时目录
RUN mkdir /root/download
WORKDIR /root/download

# 安装tomcat
RUN  \
           wget http://apache.fayea.com/tomcat/tomcat-7/v7.0.62/bin/apache-tomcat-7.0.62.tar.gz \
           && tar xvf apache-tomcat-7.0.62.tar.gz \
           && mv  apache-tomcat-7.0.62 tomcat \
           && mv  tomcat /usr/local/tomcat \
           && rm  apache-tomcat-7.0.62.tar.gz

# 安装maven
RUN  \
           wget  http://archive.apache.org/dist/maven/maven-3/3.2.2/binaries/apache-maven-3.2.2-bin.tar.gz \
           && tar xvf apache-maven-3.2.2-bin.tar.gz \
           && mv apache-maven-3.2.2 maven3 \
           && mv maven3 /usr/local/ \
           && rm apache-maven-3.2.2-bin.tar.gz \
           && export M2_HOME=/usr/local/maven3 \
           && export M2=$M2_HOME/bin \
           && export PATH=$M2:$PATH

# Remove Temp Files
Run \
           apt-get clean \
        && rm -rf /var/cache/oracle-jdk7-installer \
        && rm -f  /var/lib/apt/lists/*_dists_*  \

# 开放端口
EXPOSE 8080